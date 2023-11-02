# JSON LD Transformer

This Python library applies [SHACL rules](https://www.w3.org/TR/shacl-af/#rules) to an input [RDFLib Graph](https://rdflib.readthedocs.io/en/stable/apidocs/rdflib.html#graph), then serializes the output Graph in a clean JSON structure by applying a [JSON-LD framing](https://www.w3.org/TR/json-ld11-framing/) specification.

## Prerequisites

- Python 3.10+
- Poetry. To install and use Poetry, please refer to https://python-poetry.org/

## Usage

1. Clone the code

2. Install dependencies with poetry

```Shell
  poetry install
```

3. To make a small test, run the following:

```Shell
poetry run python3.10 jsonldtransformer/Cli.py --rules rules/datacube-2-statdcatap.ttl  --frame rules/framing-context.jsonld --data tests/small-test-data/input.ttl --output output.json
```

## Python integration

See in Cli.py for an example of how to call the transformer. This boils down to the following:

```python
# 1. Read SHACL rules Graph
graph_rules = Graph().parse(...)

# 2. Read JSON-LD framing spec
frame = json.loads(...)

# 3. Create new transformer
transformer = JsonLdTransformer(graph_rules,frame)

# 4. Read input RDF data Graph
data_graph = Graph().parse(...)

# 5. Apply data conversion rules and JSON-LD transformation on the input data Graph
result = transformer.transform(data_graph)
```

## Writing SHACL rules

See [this example file](https://github.com/sparna-git/jsonldtransformer/blob/main/rules/datacube-2-statdcatap.ttl) for an example of how to write rules. The important aspects when writing the rules are:
  - Declare instances of `sh:NodeShape` with a `sh:target` targetting the instances of the classes you want to transform.

```turtle
this:DataStructureDefinition_Shape
  rdf:type sh:NodeShape ;
  sh:targetClass <http://purl.org/linked-data/cube#DataStructureDefinition> ;
.
```
  
  - Attach transformation rules to this NodeShape with `sh:rule`.

```turtle
this:DataStructureDefinition_Shape
  rdf:type sh:NodeShape ;
  sh:targetClass <http://purl.org/linked-data/cube#DataStructureDefinition> ;
  sh:rule this:CreateDataset;
  sh:rule this:reify_dctLanguage;
  # other rules ...
.
```
  
  - Each rule is an instance of `sh:SPARQLRule`. Express the transformation rule as a SPARQL CONSTRUCT query in the `sh:construct` property. Each rule can refer to the prefixes defined at the top of the file using `sh:prefixes`.

```turtle
this:CreateDataset
  rdf:type sh:SPARQLRule ;
  rdfs:comment "Creates DCAT Dataset" ;
  rdfs:label "Creates DCAT Dataset" ;
  sh:construct """
      CONSTRUCT {
        $this a dcat:Dataset .
      }
      WHERE {
        $this a qb:DataStructureDefinition .
      }
      """ ;
  sh:order 1 ;
  sh:prefixes <http://data.sparna.fr/ontologies/datacube-2-statdcatap> ;
.
```



## Development Note

To run ruff, call:

```Shell
poetry run ruff check .
```
