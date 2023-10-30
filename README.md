

## Installation Poetry

1. Linux, macOS, Windows (WSL)
	
'''

		curl -sSL https://install.python-poetry.org | python3 -
	
 ''' 

Windows 

	(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | py -

3. Add Poetry to your PATH

'''Shell
	~/Library/Application Support/pypoetry/venv/bin/poetry on MacOS.
	~/.local/share/pypoetry/venv/bin/poetry on Linux/Unix.
	%APPDATA%\pypoetry\venv\Scripts\poetry on Windows.
	$POETRY_HOME/venv/bin/poetry if $POETRY_HOME is set.
'''

4. Use Poetry
	
	Once Poetry is installed and in your $PATH, you can execute the following:

	'''
		poetry --version

	'''

	If you see something like Poetry (version 1.2.0), your install is ready to use!


## Usage

4. Created the project setup

	'''
		poetry new <Project Name>
	'''

	This will create the <Project Name> directory with the following content:

	<Project Name>

	├── pyproject.toml
	├── README.md
	├── poetry_demo
	│   └── __init__.py
	└── tests
	    └── __init__.py


5. 
