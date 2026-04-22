# Rust Speedup Tour

> This document is for contributors who already know Python, know very little Rust, and want to answer four practical
questions:

1. What code is inheri

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# rmarc Rust Speedup Code Review and Architecture Tour

This document is for contributors who already know Python, know very little Rust, and want to answer four practical
questions:

1. What code is inherited from `pymarc`, and what code is new in `rmarc`?
2. How does a MARC record move through the Python and Rust layers?
3. Why is the Rust-backed path faster?
4. What should we trust already, and what should we still review carefully?

The short version is:

- `rmarc` keeps the public `pymarc` object model in Python: `Record`, `Field`, `RawField`, `MARCReader`, writers, JSON,
  XML, and convenience properties.
- `rmarc` moves the hot byte-crunching work into Rust:
    - binary MARC decode
    - binary MARC encode
    - MARC-8 to Unicode conversion
- Python still owns the user-facing API, error classes, and most object construction.
- Rust is used as an implementation detail, not as a new public API model.

That design choice matters. It keeps compatibility high, reduces PyO3 complexity, and explains both the speedups and the
remaining bottlenecks.

## Repository map

The parts that matter most for the speedup work are:

```text
python/rmarc/
├── __init__.py
├── reader.py
├── record.py
├── field.py
├── marc8.py
├── writer.py
└── _rmarc.pyi

src/
├── lib.rs
├── marc_codec.rs
├── marc8.rs
└── marc8_mapping.rs

bench/
├── bench_core.py
└── generate_data.py

spec/
├── phase3_rustification.md
├── phase4_performance.md
└── benchmarks.md
```

Use this mental model:

- `python/rmarc` is the compatibility layer and public surface area.
- `src/` is the acceleration engine.
- `bench/` tells you what the author considered performance-critical.
- `spec/` tells you the intended migration strategy and how closely the current code matches that plan.

## Big-picture architecture

The core idea is not "rewrite pymarc in Rust."

The real idea is:

1. Preserve the `pymarc` Python API.
2. Identify the small number of loops that do most of the CPU work.
3. Move only those loops into Rust

*[truncated — see source for full prompt]*