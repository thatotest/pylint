# pylint
Testing git-pylint-commit-hook


Pre-commit hook for Git checking Python code quality. The hook will check files ending with .py or that has a she bang (#!) containing python.

The script will try to find pylint configuration files in the order determined by pylint. It also looks for a [pre-commit-hook] section in the pylint configuration for commit hook specific options.

Installation

Install via PyPI

pip install git-pylint-commit-hook
Usage

The commit hook will automatically be called when you are running git commit. If you want to skip the tests for a certain commit, use the -n flag, git commit -n.

Configuration

Settings are loaded by default from the .pylintrc file in the root of your repo.

[pre-commit-hook]
command=custom_pylint
params=--rcfile=/path/to/another/pylint.rc
limit=8.0
command is for the actual command, for instance if pylint is not installed globally, but is in a virtualenv inside the project itself.

params lets you pass custom parameters to pylint

limit is the lowest value which you want to allow for a pylint score. Any lower than this, and the script will fail and won't commit.

Any of these can be bypassed directly in the pre-commit hook itself. You can also set a different default place to look for the pylintrc file.

Running tests

The test suite requires nose2 to be installed. Install it with pip install nose2, then run the tests by executing the following command (in the project root folder):

nose2
Requirements

This project supports Python 2.7 and Python 3.5. Please install other requirements via

pip install -r requirements.txt
