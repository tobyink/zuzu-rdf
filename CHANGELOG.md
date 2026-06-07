# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project roughly adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added

- Turtle support for object lists, predicate-object lists, blank-node
  property lists, RDF collections, numeric literals, and boolean literals.
- Store schema verification, backend label validation, and quad lookup
  indexes for first-time schema installs.
- SPARQL 1.1 Query support for `SELECT`, `ASK`, `CONSTRUCT`,
  `DESCRIBE`, graph patterns, joins, `OPTIONAL`, `UNION`, `MINUS`,
  `FILTER` and `EXISTS`, `VALUES`, `BIND`, grouping, aggregates,
  projection expressions, property paths, dataset clauses, solution
  modifiers, built-in functions, and `SERVICE` queries.
- Author-gated MySQL/PostgreSQL store tests and local W3C-style parser,
  serializer, store, and SPARQL fixtures.
- RDF/XML support for typed node elements, `xml:base`, `xml:lang`,
  `rdf:ID`, `rdf:nodeID`, property attributes, `parseType` resource,
  collection, and XML literal forms, RDF lists, `rdf:li`, and RDF/XML
  reification.
- Author-gated W3C RDF 1.1 RDF/XML positive and negative syntax tests.
- Author-gated W3C SPARQL 1.1 Query syntax tests and W3C evaluation
  wrappers for aggregates, `BIND`, `VALUES`, casts, `CONSTRUCT`,
  `EXISTS` and negation, built-in functions, grouping, project
  expressions, property paths, and subqueries.
- Author-gated W3C SPARQL 1.1 Update syntax tests.
- SPARQL syntax parsing entrypoint via `sparql_parse`, with
  `sparql_parse_query` retained as an alias.
- SPARQL Update syntax parsing via the shared SPARQL parser. Update
  execution is intentionally left for a later stage.
- Semantic Web framework roadmap document covering major future RDF,
  SPARQL, validation, reasoning, store, and ergonomics work.
- Turtle and N-Triples compliance tests for strict N-Triples grammar,
  Turtle long strings, single-quoted strings, escaped prefixed names,
  base IRI resolution, numeric forms, and N-Triples serializer escapes.
- Author-gated W3C RDF 1.1 Turtle, N-Triples, and N-Quads syntax
  manifests and fixtures.
- Public RDF graph and dataset utilities for canonicalization,
  isomorphism, set operations, patching, blank-node relabelling,
  skolemization, and scoped blank-node allocation.
- Store transaction helpers, bulk loading, named graph management APIs,
  explicit find, statistics, diagnostics, and query planning explanation.
- SPARQL Update execution for data updates, modify operations, graph
  management, `WITH`, `LOAD`, transactional execution, prepared updates,
  and SPARQL Protocol update requests.
- SPARQL result serializers for XML, JSON, CSV, and TSV, plus streaming
  parser and serializer APIs for large inputs and outputs.
- SPARQL diagnostics and prepared query APIs.
- SPARQL Protocol HTTP(S) client for remote query and update endpoints,
  returning the same result shapes as local SPARQL execution.
- `RDFSchemaStore` with RDFS subclass, subproperty, domain, range, and
  type entailment.
- RDF Schema, OWL, RDF, and XSD vocabulary helpers, datatype
  canonicalization and value-space comparison helpers, prefix registries,
  an RDF builder DSL, and lightweight resource wrappers.
- Example scripts for parser/store/SPARQL and builder/resource workflows,
  plus a published compliance matrix.

### Fixed

- Language-tagged literals now use `rdf:langString` internally and
  serialize without an invalid explicit datatype.
- The temporary `tests/runner.zzs` harness was removed; `zuzuzoo`
  discovers `.zzs` tests under `tests` automatically.
- SPARQL joins now compare repeated variables against the actual dynamic
  binding key instead of the literal key name.
- SPARQL W3C result comparisons now cover exact term values, graph
  results, optional bindings, blank-node isomorphism, result ordering,
  and expected error cases.
- N-Triples and N-Quads parsing now reject Turtle-only syntax such as
  directives, bare `a`, booleans, numerics, relative IRIs, and
  single-quoted strings.
- Turtle parsing now keeps `a` as `rdf:type` only in predicate position,
  requires the correct directive terminator style, resolves base IRIs
  using RFC-style path handling, and handles long strings, single-quoted
  strings, Unicode escapes, stricter language tags, leading-dot decimals,
  and escaped prefixed-name punctuation.
- Turtle parsing now handles SPARQL-style case-insensitive directives,
  sole blank-node property lists, repeated semicolons, escaped `%` in
  local names, local-name dot runs, stricter local-name starts, invalid
  decoded IRI escapes, and RFC 3986 IRI resolution with preserved empty
  path segments.
- N-Triples serialization now escapes control characters and illegal IRI
  characters, escapes datatype IRIs, and rejects blank node labels that
  cannot be represented in N-Triples.
- SPARQL prefix stripping now preserves same-line query and update bodies
  after `BASE` and `PREFIX` declarations.

## 0.0.1 - 2026-06-06

*First release.*
