# Semantic Web Framework Base

This document tracks larger features that would make this distribution a
stronger RDF, Semantic Web, and Linked Data framework base.

## Core RDF

- [ ] RDF-star or quoted triples support, if RDF 1.2 support becomes a goal. (Out of scope. Potential future.)
- [x] Public canonicalization and graph isomorphism APIs beyond test helpers.
- [x] Dataset-level APIs for merging, diffing, patching, copying, moving, and
  clearing named graphs.
- [x] Better blank node handling, including scoped allocation, stable
  relabelling, and skolemization.
- [x] Transaction helpers around store mutations.

## Parsers And Serializers

- [x] Full Turtle, N-Triples, N-Quads, and RDF/XML compliance hardening.
- [ ] TriG parser and serializer for named graph datasets. (Out of scope. External distribution.)
- [ ] JSON-LD support for practical interoperability. (Out of scope. External distribution.)
- [x] SPARQL result serializers for XML, JSON, CSV, and TSV result formats.
- [x] Streaming parser and serializer interfaces for large files.

## SPARQL

- [x] SPARQL Update execution.
- [ ] Federated `SERVICE` execution over HTTP endpoints. (Out of scope.)
- [x] SPARQL Protocol support for query and update endpoints.
- [x] Query planning, index selection, and explain/debug hooks for larger
  stores.
- [x] Better diagnostics for parse-time and query-time errors.

## Schema, Validation, And Reasoning

- [x] RDFS entailment for subclass, subproperty, domain, range, and type
  inference. Subclass of RDFStore: RDFSchemaStore.
- [ ] Optional OWL RL-style rule reasoning. (Out of scope.)
- [ ] SHACL validation. (Out of scope.)
- [x] RDF Schema and OWL vocabulary helpers.
- [x] Datatype value-space support for comparison and canonicalization,
  especially XSD numeric, date, and time types.

## Store Layer

- [x] Bulk loading APIs.
- [x] Prepared query and update APIs.
- [x] Store statistics and backend-specific diagnostics.
- [ ] Backend-specific migrations and schema versioning. (Out of scope.)
- [x] Concurrent access behaviour tests.
- [x] Named graph management APIs.
- [ ] Optional full-text index hooks. (Out of scope.)

## Developer Ergonomics

- [x] Namespace and prefix registry helpers.
- [x] RDF builder DSL for concise graph construction.
- [x] Lightweight resource wrappers or object mapping.
- [x] More examples for parser, store, and SPARQL workflows.
- [x] A published compliance matrix for W3C test groups.
