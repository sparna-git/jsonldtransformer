
## Installation Poetry

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


## Development Note

To run ruff, call:

```Shell
poetry run ruff check .
```
