# Faq

> ## Why another framework?

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# FAQ

## Why another framework?

There are a number of excellent frameworks for performing mapping and data transformations.
The LinkML Transformer framework was born out of a need for a framework that:

- was not inherently tied to:
     - a particular serialization format (e.g. RDF, JSON, ...)
     - a particular programming language (e.g. Python, Java, ...)
     - a particular database system or database language (e.g. PostgreSQL or SQL or SPARQL)
     - not tied to a particular kind of transformation (e.g. ORM or Tables to RDF)
- was a natural fit for the LinkML data modeling framework
- was declarative and easy to perform machine reasoning over
- is simple for simple use cases

The core idea is that the **TransformationSpecification** is a declarative intermediate representation
that can be executed by different backends. Today the primary backend is the Python ObjectTransformer
(which supports the full feature set). An experimental SQL compilation backend (DuckDB) supports a
limited subset for set-based database transformations.

In its current state, this framework is less powerful and expressive than many other frameworks
or methodologies for performing transformations. If you need to perform complex data transformations,
you might be better off using an expressive query language like SPARQL or SQL, or even just coding
transformations directly in a programming language or library like Python or Pandas (but note that
even for the coding use case, the LinkML Transformer framework can be useful as a standard way
of *documenting* transformations).

Currently the main use case for this framework is *mostly isomorphic* transformations, with lightweight
manipulations. These lend themselves well to a declarative framework. Uses cases that are a particularly good fit
involve mapping between data-dictionary like standards, with large numbers of metadata elements, where these
elements can often be mapped one-to-one, or with simple manipulations (e.g. unit conversions)

*[truncated — see source for full prompt]*