# Index

> LinkML Map is a framework for specifying and executing declarative mappings between data models.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# LinkML-Map

LinkML Map is a framework for specifying and executing declarative mappings between data models.

The core of LinkML Map is the **TransformationSpecification** — a YAML-based language for describing
how to map one data model to another. This specification is independent of how the transformation
is executed or what format the data lives in.

Features:

- YAML-based lightweight transformation syntax
- Python library for executing mappings on data files
- Streaming support for large tabular datasets (TSV/CSV)
- Multiple text serialization formats (YAML, JSON, JSONL, TSV, CSV)
- Derivation of target (implicit) schemas, allowing easy customization of data models (*profiling*)
- Simple YAML dictionaries for simple mappings
- Automatic unit conversion
- Use of subset of Python to specify complex mappings
- Visualizations of mappings
- Mappings are reversible (provided all expressions used are reversible)
- Compatibility with SSSOM

## Architecture

The TransformationSpecification acts as a declarative intermediate representation that can be
interpreted by different execution backends:

- **ObjectTransformer** (Python) — interprets the spec row-by-row, supports the full feature set
  including Python expressions, unit conversion, and cross-class lookups.
- **SQLCompiler / DuckDBTransformer** (SQL) — compiles the spec to SQL for set-based execution.
  This backend is **experimental** and supports a limited subset of the specification today.
  See the [SQL Compilation tutorial](examples/Tutorial-SQLCompiler.ipynb) for current capabilities.

The output serialization formats (YAML, JSON, JSONL, TSV, CSV) are intentionally limited to
text-based representations of transformed data. For loading results into analytical stores
(DuckDB, Parquet, databases), use the appropriate downstream tool — e.g., DuckDB's native
`read_json()` or `read_csv()` functions work directly on linkml-map output files.

This documentation is available at:

- [linkml.io/linkml-map/](https://l

*[truncated — see source for full prompt]*