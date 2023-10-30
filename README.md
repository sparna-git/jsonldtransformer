
## Installation Poetry

## System requirements

Poetry requires Python 3.8+. It is multi-platform and the goal is to make it work equally well on Linux, macOS and Windows.

## Install Poetry

1. Linux, macOS, Windows (WSL)
	
```shell
curl -sSL https://install.python-poetry.org | python3 -
```

Windows

```shell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -
```

2. Add Poetry to your PATH

The installer creates a poetry wrapper in a well-known, platform-specific directory:

```shell
- ~/Library/Application Support/pypoetry/venv/bin/poetry on MacOS.
- ~/.local/share/pypoetry/venv/bin/poetry on Linux/Unix.
- %APPDATA%\pypoetry\venv\Scripts\poetry on Windows.
- $POETRY_HOME/venv/bin/poetry if $POETRY_HOME is set.
```

If this directory is not present in your $PATH, you can add it in order to invoke Poetry as poetry.

3. Use Poetry
	
Once Poetry is installed and in your $PATH, you can execute the following:

```shell
poetry --version
```

If you see something like Poetry (version 1.2.0), your install is ready to use!

## Usage

4. Created the project setup

```shell
poetry new jsonldtransformer
```

This will create the <Project Name> directory with the following content:
	
	jsonldtransformer
	├── pyproject.toml
	├── README.md
	├── jsonldtransformer
	│   └── __init__.py
	└── tests
	    └── __init__.py     	

5. Copy all python files to <Project Name> sud-directory

```Shell
	jsonldtransformer
	├── pyproject.toml **
	├── README.md
	├── jsonldtransformer
	│   └── __init__.py
	│   └── Cli.py **Python file**
	│   └── JsonLdTransformer.py **Python file**
	└── tests
	    └── __init__.py
```

6. Copy pyproject.toml file and install dependencies


```Shell
  poetry install
```

 ## Using poetry run
7. To run your script simply use:

```Shell
poetry run python your_script.py.
```

8. 
   
