# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project roughly adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 0.0.2 - 2026-06-08

### Added

- Added shared `RdfParser` and `RdfSerializer` traits. (tobyink)
- Added store-level `serialize` and `serialize_to` methods. (tobyink)
- Added `query_rdf.zzs` for running SPARQL queries against existing
  stores or temporary stores loaded from RDF input. (tobyink)
- Added `std/data/json` as an explicit dependency. (tobyink)

### Changed

- Changed status to "stable". (tobyink)
- Improved RDF parser, serializer, command-line script, and store
  behaviour. (tobyink)
- Updated README documentation and tests. (tobyink)

## 0.0.1 - 2026-06-08

*First release.*
