# Benchmarks

> ## Purpose

Every Rust migration in Phase 3 must prove it's faster. This document defines the
benchmarks, how to run them, and what "faster" means.

-

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Benchmark Plan

## Purpose

Every Rust migration in Phase 3 must prove it's faster. This document defines the
benchmarks, how to run them, and what "faster" means.

---

## Benchmark Scenarios

### Scenario 1: Read and Iterate (the common case)

Open a MARC file, iterate all records, access title field. This is what most pymarc
users do.

```python
def bench_read_iterate(path):
    from rmarc import MARCReader
    with open(path, "rb") as fh:
        reader = MARCReader(fh)
        for record in reader:
            if record:
                _ = record.title
```

**Measures:** Full pipeline — file I/O, binary parsing, field construction, property
access.

### Scenario 2: Decode Only (isolates parsing)

Parse a pre-read byte blob into a Record. No file I/O.

```python
def bench_decode(data_blob):
    from rmarc import Record
    record = Record(data_blob)
```

**Measures:** `decode_marc()` in isolation.

### Scenario 3: Encode / Round-Trip

Parse then serialize back to bytes.

```python
def bench_roundtrip(data_blob):
    from rmarc import Record
    record = Record(data_blob)
    _ = record.as_marc()
```

**Measures:** `decode_marc()` + `as_marc()`.

### Scenario 4: MARC-8 Conversion

Convert MARC-8 encoded data to Unicode.

```python
def bench_marc8(marc8_lines):
    from rmarc import marc8_to_unicode
    for line in marc8_lines:
        _ = marc8_to_unicode(line)
```

**Measures:** `marc8_to_unicode()` throughput on the 1515-line test corpus.

### Scenario 5: Field Access (micro-benchmark)

Create a record, access subfields by code. Tests Python object overhead.

```python
def bench_field_access(record):
    for field in record.get_fields("245", "100", "650"):
        _ = field.get("a")
        _ = field.value()
```

**Measures:** Python object traversal. Baseline for "is Rust even relevant here?"

### Scenario 6: Bulk File Processing

Process a large (multi-MB) MARC file end-to-end. This is the "real world" scenario.

```python
def bench_bulk(path):
    from rm

*[truncated — see source for full prompt]*