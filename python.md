Command|Description
---|---
export PYTHONDONTWRITEBYTECODE=1|prevent python from writing pyo and pyc files
pip install *package*|install package
pip install --upgrade *package*|upgrade package
pip freeze > requirements.txt|write packages in current environment to requirements file
pip install -r requirements.txt|install dependencies from requirements file
pip list|list installed packages
pip uninstall *package*|uninstall package
pydoc3 -p *port*, python -m pydoc -p *port*|start local http server serving python documentation on specified port
python3 -m venv *ENV*<br>source *ENV*/bin/activate<br>...<br>deactivate|basic virtual environment usage
reload(*module*)|Reload module. Useful when debugging with interpreter and editing the source. Import required: **from importlib import reload**
_|use "_" as a throwaway variable. Stores result of last calculation in interpreter
