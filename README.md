# rdf

RDF, Linked Data, and SPARQL tools for ZuzuScript.

This trial distribution provides:

- RDF term and quad value objects.
- Parsers for N-Triples, N-Quads, Turtle, TriG, and RDF/XML.
- Serializers for N-Triples, N-Quads, Turtle, TriG, RDF/XML, and SPARQL result
  sets.
- A `std/db`-backed quad store for SQLite, MySQL, and PostgreSQL.
- SPARQL 1.1 Query parsing and execution over stores.
- SPARQL 1.1 Update parsing and execution.
- SPARQL Protocol request handling, HTTP(S) client support, and SPARQL
  result serializers, including Turtle and RDF/XML graph results.
- RDFS entailment, datatype helpers, prefix registries, builders, and
  resource wrappers.

The first implementation is pure ZuzuScript and has no dependencies beyond
the Zuzu interpreter and stdlib. The SPARQL parser accepts SPARQL 1.1
Query and Update syntax. Query execution covers `SELECT`, `ASK`,
`CONSTRUCT`, `DESCRIBE`, graph patterns, joins, `OPTIONAL`, `UNION`,
`MINUS`, `FILTER` and `EXISTS`, `VALUES`, `BIND`, grouping, aggregates,
projection expressions, property paths, dataset clauses, solution
modifiers, built-in functions, and `SERVICE` queries. SPARQL Update
execution covers data updates, modify operations, graph management
operations, local and HTTP `LOAD`, prepared updates, and protocol update
requests.

Remote SPARQL Protocol endpoints can be queried with
`SPARQLProtocolClient`; results are parsed into the same dictionary shapes
returned by local `sparql_query` and `sparql_update` calls.

RDF syntax support includes author tests for the official W3C RDF 1.1
RDF/XML, Turtle, TriG, N-Triples, and N-Quads manifests. RDF/XML covers typed
node elements, `xml:base`, `xml:lang`, `rdf:ID`, `rdf:nodeID`, property
attributes, `parseType` resource, collection, and XML literal forms, RDF
lists, `rdf:li`, and RDF/XML reification.

SPARQL author tests vendor the W3C SPARQL 1.1 Query and Update syntax
conformance fixtures. Syntax runners cover the W3C positive and negative
SPARQL 1.1 Query and Update syntax tests. Evaluation wrappers cover
vendored W3C SPARQL 1.1 Query suites for aggregates, `BIND`, `VALUES`,
casts, `CONSTRUCT`, `EXISTS` and negation, built-in functions, grouping,
project expressions, property paths, and subqueries, with exact
`SELECT`, `ASK`, and graph-result comparisons where applicable.

## Example

```zzs
from rdf import RDFStore, TurtleParser, TriGSerializer, sparql_query;

let store := RDFStore.temp();
store.install_schema();
store.add_quads(( new TurtleParser() ).parse_string("""
@prefix ex: <http://example.com/> .
ex:s ex:p "value" .
"""));

let result := sparql_query(store, """
PREFIX ex: <http://example.com/>
SELECT ?o WHERE { ex:s ex:p ?o . }
""");

let trig := ( new TriGSerializer() ).serialize(store.find());
```

Use `sparql_parse` to parse Query or Update syntax without executing it:

```zzs
let parsed := sparql_parse("""
INSERT DATA { <http://example.com/s> <http://example.com/p> "value" . }
""");
```

The distribution includes two command-line helpers. `parse_rdf.zzs` reads RDF
from one or more files, or from STDIN when no files are given, loads it into an
RDF store, and can optionally dump the whole store:

```sh
zuzu scripts/parse_rdf.zzs --trig --sqlite data.sqlite data.trig
zuzu scripts/parse_rdf.zzs --turtle --stdout data.ttl
zuzu scripts/parse_rdf.zzs --turtle --base https://example.com/doc --stdout data.ttl
zuzu scripts/parse_rdf.zzs --turtle --graph https://example.com/graph data.ttl
zuzu scripts/parse_rdf.zzs --replace --sqlite data.sqlite data.ttl
```

`serialize_rdf.zzs` serializes an existing store and writes to STDOUT by
default:

```sh
zuzu scripts/serialize_rdf.zzs --sqlite data.sqlite --trig-out
zuzu scripts/serialize_rdf.zzs --sqlite data.sqlite --turtle-out --prefix ex=https://example.com/
```

Use `--parser=module.Class`, `--serializer=module.Class`, and
`--store=module.Class` to load compatible third-party classes dynamically.

Use `sparql_update` to execute Update operations transactionally:

```zzs
sparql_update(store, """
PREFIX ex: <http://example.com/>
INSERT DATA { ex:s ex:p "value" . }
""");
```

Parsers are classes. Use `parse_string` to return quads, or `parse_file`
with `into: store` to load directly into a store:

```zzs
let parser := new RdfXmlParser();
parser.parse_file( somepath, into: store );
```

Higher-level helpers are available for common application code:

```zzs
from rdf import RDFBuilder, RDFResource, rdf_iri, rdf_type;

let builder := new RDFBuilder();
builder
	.prefix( "ex", "http://example.com/" )
	.triple( "ex:alice", rdf_type(), "ex:Person" )
	.triple( "ex:alice", "ex:name", builder.literal("Alice") );

builder.add_to(store);

let alice := new RDFResource(
	store: store,
	term: rdf_iri("http://example.com/alice"),
);
say alice.value(rdf_iri("http://example.com/name")).get_value();
```

See `COMPLIANCE.md` for the current parser, serializer, SPARQL, store,
and framework compliance matrix.

## Notes

The normal test suite uses SQLite through `DB.temp()`. MySQL and
PostgreSQL are intended to be covered by author tests using local
`zuzutest` databases, following the stdlib `std/db` convention. Set
`RDF_AUTHOR_MYSQL=1` or `RDF_AUTHOR_POSTGRESQL=1` under
`AUTHOR_TESTING=1` to run those backend checks. DSNs may be overridden
with `RDF_AUTHOR_MYSQL_DSN` and `RDF_AUTHOR_POSTGRESQL_DSN`.

`zuzuzoo` discovers every `.zzs` file under `tests`, so there is no
separate test runner script in the distribution.
