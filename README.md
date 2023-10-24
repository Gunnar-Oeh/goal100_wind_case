# goal100_wind_case

Starting-point for the necessary steps of the ETL of fetching the Windpower-data from the BNetzA Markstammdatenregister in XML, parsing those in python, transforming and testing and uploading into a PostGIS-Database.

## Requirements:

- pyenv with Python: 3.10

### Setup

Use the requirements file in this repo to create a new environment.

```BASH
make setup
```

or

```BASH
pyenv local 3.10.12
python -m venv .venv
source .venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
source .venv/bin/activate
```
