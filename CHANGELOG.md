# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project roughly adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## 0.0.3 - 2026-06-12

### Fixed

- SPARQL: blank lines are no longer stripped from query bodies, so
  long-quoted literals containing them survive parsing. (tobyink)
- SPARQL: relative IRIs in queries are resolved against `BASE` per
  RFC 3986 instead of by concatenation. (tobyink)
- SPARQL: `BOUND()` results are now reduced to a boolean portably;
  on zuzu.pl a bare `false` is not `instanceof Boolean`, which made
  `FILTER (!BOUND(?x))` always fail. (tobyink)
- SPARQL: `GROUP_CONCAT` separators containing `;` are parsed
  correctly. (tobyink)
- `RDFStore.temp()` enables `sqlite_unicode` so text round-trips
  losslessly on zuzu.pl. (tobyink)
- Prefixed-name expansion keeps colons in the local part (e.g.
  `ex:column:test`); zuzu-js truncates limit-2 splits. (tobyink)
- Replaced quote characters in regex literals with `\x22`/`\x27`
  escapes; literal quotes inside regexes corrupt the zuzu-js module
  tokenizer, silently dropping later functions. (tobyink)
- Replaced `X != null` comparisons with `not (X == null)` throughout;
  the former throws on zuzu-js when X is a non-numeric string. With
  these changes the Turtle and SPARQL engines work on zuzu-js.
  (tobyink)

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
