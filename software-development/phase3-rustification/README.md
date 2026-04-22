# Phase3 Rustification

> ## Current State (End of Phase 2)

We have a fully working pymarc-compatible Python library (`rmarc`) that passes all 171
pymarc tests. The architectu

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Phase 3: Rustification Plan

## Current State (End of Phase 2)

We have a fully working pymarc-compatible Python library (`rmarc`) that passes all 171
pymarc tests. The architecture is:

```
python/rmarc/
├── __init__.py          # re-exports everything
├── constants.py         # LEADER_LEN, SUBFIELD_INDICATOR, etc.
├── exceptions.py        # 14 exception types
├── leader.py            # Leader class
├── field.py             # Field, Subfield, Indicators, RawField
├── record.py            # Record, decode_marc, as_marc, convenience props
├── reader.py            # MARCReader, JSONReader, MARCMakerReader
├── writer.py            # MARCWriter, JSONWriter, TextWriter, XMLWriter
├── marc8.py             # MARC8ToUnicode, marc8_to_unicode
├── marc8_mapping.py     # ~17K lines of character mapping data
├── marcxml.py           # XML parse/serialize
├── marcjson.py          # JSON parse/serialize
└── _rmarc.pyd           # Rust extension (currently: version() only)
```

Everything is pure Python except the stub `_rmarc` extension. The goal of Phase 3 is
to move performance-critical code into Rust while keeping the Python API unchanged.

---

## Guiding Principles

1. **Measure first.** Every Rust migration must show a measurable speedup in the
   benchmark suite before it replaces the Python path.
2. **Incremental.** Each Rust component is optional — the Python fallback stays until
   the Rust version is proven correct and faster.
3. **No API changes.** The Python-facing interface is frozen. Rust is an implementation
   detail invisible to users.
4. **Test parity.** All 171 existing tests must continue to pass at every step. Rust
   unit tests are additive.

---

## Where Rust Helps (and Where It Doesn't)

### High-value targets (CPU-bound, called millions of times)

| Component | Why it's hot | Expected speedup |
|---|---|---|
| `decode_marc()` | Parses binary MARC: byte slicing, directory parsing, field extraction. Called once per record, but does a lot of byte-level w

*[truncated — see source for full prompt]*