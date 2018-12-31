Command|Description
---|---
export PYTHONDONTWRITEBYTECODE=1|prevent python from writing pyo and pyc files
pip install *package*|install package
pip install --upgrade *package*|upgrade package
pip freeze > requirements.txt|write packages in current environment to requirements file
pip install -r requirements.txt|install dependencies from requirements file
pip list|list installed packages
pip uninstall *package*|uninstall package
pydoc -p *port*|start local http server serving python documentation on specified port
virtualenv *ENV*<br>source *ENV*/bin/activate<br>...<br>deactivate|basic virtualenv usage. if windows, activate by running *ENV*/Scripts/activate
virtualenv -p python3 *ENV*<br>source *ENV*/bin/activate<br>...<br>deactivate|virtualenv usage with specified python interpreter
python3 -m venv *ENV*<br>source *ENV*/bin/activate<br>...<br>deactivate|basic virtual environment usage
_|use "_" as a throwaway variable, stores result of last calculation in interpreter
reload(*module*)|Reload module. Useful when debugging with interpreter and editing the source. If python3, import required: **from importlib import reload**
