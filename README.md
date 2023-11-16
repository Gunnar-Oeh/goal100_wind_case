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

The .env file is build like this and saved within the root directory of the repository
```BASH
DB_USER=user_name                               # unquoted
# DB_USER_READONLY= read_only_user_name         # unquoted
DB_PASSWORD=password                            # unquoted
# DB_PASSWORD_READONLY=read_only_password       # unquoted 
DB_HOST="db.some_letters.supabase.co"           # quoted url
DB_PORT=1234                                    # standard port. not 1234
DB_NAME=db_name                                 # db_name unquoted
SSL_CERT_PATH="/path_to/crtfile.crt"            # path to .crt file
```
