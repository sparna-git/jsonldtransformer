
## Installation Poetry

## System requirements

Poetry requires Python 3.8+. It is multi-platform and the goal is to make it work equally well on Linux, macOS and Windows.

## Install Poetry

1. Linux, macOS, Windows (WSL)
	


		curl -sSL https://install.python-poetry.org | python3 -
	
 

Windows 

	(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -

2. Add Poetry to your PATH

 The installer creates a poetry wrapper in a well-known, platform-specific directory:

   	- ~/Library/Application Support/pypoetry/venv/bin/poetry on MacOS.
 	- ~/.local/share/pypoetry/venv/bin/poetry on Linux/Unix.
  	- %APPDATA%\pypoetry\venv\Scripts\poetry on Windows.
   	- $POETRY_HOME/venv/bin/poetry if $POETRY_HOME is set.
    
If this directory is not present in your $PATH, you can add it in order to invoke Poetry as poetry.

4. Use Poetry
	
	Once Poetry is installed and in your $PATH, you can execute the following:

	'''

		poetry --version

	'''

	If you see something like Poetry (version 1.2.0), your install is ready to use!


## Usage

4. Created the project setup

	

		poetry new <Project Name>
	

	This will create the <Project Name> directory with the following content:

	<p>
	<Project Name>
	├── pyproject.toml
	├── README.md
	├── poetry_demo
	│   └── __init__.py
	└── tests
	    └── __init__.py

     	</p>

5. Copy all python files to <Project Name>/ sud-directory

	<Project Name>
	├── pyproject.toml
	├── README.md
	├── <Project Name>
	│   └── __init__.py
	│   └── File.py * Python file
	│   └── File2.py * Python file
	└── tests
	    └── __init__.py

6. Copy pyproject.toml file and update poetry environment 

	'''

		poetry install or poetry update
	'''
