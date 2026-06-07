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

## 0.0.1 - 2026-06-06

*First release.*
