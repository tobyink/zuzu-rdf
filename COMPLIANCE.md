# Compliance Matrix

This matrix summarizes the conformance surface covered by this distribution's
normal and author-gated tests.

## RDF Syntax

| Area | Status | Test Coverage |
| --- | --- | --- |
| N-Triples parser | Implemented | Author-gated W3C RDF 1.1 N-Triples positive and negative syntax manifests plus strict local compliance tests for grammar edges, escapes, comments, invalid Turtle-only syntax, and serializer round trips. |
| N-Quads parser | Implemented | Author-gated W3C RDF 1.1 N-Quads positive and negative syntax manifests plus strict local compliance tests for graph terms, default graph handling, invalid Turtle-only syntax, and round trips. |
| Turtle parser | Implemented | Author-gated W3C RDF 1.1 Turtle eval, positive syntax, negative syntax, and negative eval manifests plus local tests for directives, base IRI resolution, prefixed-name escapes, collections, blank-node property lists, literals, numerics, and booleans. |
| TriG parser | Implemented | Author-gated W3C RDF 1.1 TriG eval, positive syntax, negative syntax, and negative eval manifests plus local tests for default graphs, named graphs, blank graph labels, collections, and accepted graph-block variants. |
| RDF/XML parser | Implemented | Author-gated W3C RDF 1.1 RDF/XML positive and negative syntax manifests plus focused local non-ASCII and feature tests. |
| N-Triples serializer | Implemented | Local tests for escaped controls, escaped IRI characters, datatype IRIs, and invalid blank node labels. |
| N-Quads serializer | Implemented | Local round-trip and graph serialization tests. |
| Turtle serializer | Implemented | Local tests for prefix emission, MockTurtleSoup-style subject and predicate ordering, compact RDF lists, nested single-use blank nodes, and parser round trips. |
| TriG serializer | Implemented | Local tests for example-3 style default output, `wrap_default`, `graph_keyword`, named graph blocks, and parser round trips. |
| RDF/XML serializer | Implemented | Local tests for typed node elements, configured labelling predicates, nested single-use blank nodes, collection parseType output, and parser round trips. |

## SPARQL

| Area | Status | Test Coverage |
| --- | --- | --- |
| SPARQL 1.1 Query syntax | Implemented | Author-gated W3C positive and negative syntax manifests. |
| SPARQL 1.1 Query execution | Implemented | W3C-derived suites for aggregates, BIND, VALUES, casts, CONSTRUCT, EXISTS, negation, functions, grouping, project expressions, property paths, and subqueries. |
| SPARQL 1.1 Update syntax | Implemented | Author-gated W3C positive and negative Update syntax manifests. |
| SPARQL 1.1 Update execution | Implemented | Local tests for INSERT DATA, DELETE DATA, DELETE WHERE, DELETE/INSERT WHERE, WITH, CLEAR, DROP, CREATE, ADD, COPY, MOVE, LOAD parser path, transactions, and protocol update requests. |
| SPARQL Protocol | Implemented | Local tests for server-side query requests, update requests, form decoding, content negotiation, error responses, and client-side HTTP(S) query/update calls with JSON, XML, and RDF graph responses. |
| SPARQL result formats | Implemented | Local tests for XML, JSON, CSV, and TSV SELECT/ASK serialization. |

## Store And Framework APIs

| Area | Status | Test Coverage |
| --- | --- | --- |
| SQLite backend | Implemented | Normal tests use `DB.temp()`. |
| MySQL backend | Implemented | Author-gated `std/db` backend tests when `RDF_AUTHOR_MYSQL=1`. |
| PostgreSQL backend | Implemented | Author-gated `std/db` backend tests when `RDF_AUTHOR_POSTGRESQL=1`. |
| Graph isomorphism/canonicalization | Implemented | Local tests for stable blank-node relabelling and dataset comparison. |
| Graph/dataset utilities | Implemented | Local tests for union, intersection, minus, patching, graph copy/move/clear, and named graph APIs. |
| RDFS entailment | Implemented | Local tests for subclass, subproperty, domain, range, and type inference. |
| Datatype value-space helpers | Implemented | Local tests for numeric comparison and canonicalization of numeric, boolean, date, time, and dateTime lexical forms. |
| Prefix registry, builder, and resource wrappers | Implemented | Local ergonomics tests and examples. |

## Out Of Scope Here

RDF-star, JSON-LD, federated SERVICE execution beyond direct HTTP SPARQL
JSON requests, OWL RL, SHACL, store migrations, and full-text index hooks
are intentionally out of scope for this distribution or deferred to future
external distributions.
