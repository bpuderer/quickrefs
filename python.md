Command|Description
---|---
export PYTHONDONTWRITEBYTECODE=1|prevent python from writing pyo and pyc files
pip install package|install package
pip install --upgrade package|upgrade package
pip freeze > requirements.txt|write packages in current environment to requirements file
pip install -r requirements.txt|install dependencies from requirements file
pip list|list installed packages
pip uninstall package|uninstall package
virtualenv ENV<br>source ENV/bin/activate<br>...<br>deactivate|basic virtualenv usage
virtualenv -p python3 ENV<br>source ENV/bin/activate<br>...<br>deactivate|virtualenv usage with specified python interpreter
_|use "_" as a throwaway variable
