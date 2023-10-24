# goal100_wind_case

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
pip install -r requirements_dev.txt
source .venv/bin/activate
```
