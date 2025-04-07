# gcp-cook-book

## Pre-requisite Skills for the course

* Working experience using SQL is required
* Programming experience is required, preferably using Python
* Data Engineering or Data Warehousing experience
* Basic understanding of Command Line tools such as zsh

## Signing up for GCP
Let us make sure we signup for GCP using valid email id. Keep in mind that you are eligible for USD 300 credit which is valid for 3 months.

## Check for the Python installation
```
python3.9
```
Create a virtul env in the working directory
```
python3.9 -m venv de_env
```
Activate the virtual env
```
source myenv/bin/activate
```
Install Packages
```
pip install package
```
Save installed packages to requirements.txt
```
pip freeze > requirements.txt
```
Install Packages from a File
```
pip install -r requirements.txt
```

## Setup Google Cloud SDK
Click [here](https://cloud.google.com/sdk/docs/install) to go to the instructions related to setting up gcloud CLI.

## gsutil list
gs://de_analytics/

## gsutil ls
gs://de_analytics/

## gsutil ls gs://de_analytics/
gs://de_analytics/retail_db/

## gsutil ls -r gs://de_analytics/
gs://de_analytics/retail_db/:
gs://de_analytics/retail_db/create_db_tables_pg.sql
gs://de_analytics/retail_db/load_db_tables_pg.sql
gs://de_analytics/retail_db/schemas.json

gs://de_analytics/retail_db/categories/:
gs://de_analytics/retail_db/categories/part-00000

gs://de_analytics/retail_db/customers/:
gs://de_analytics/retail_db/customers/part-00000

gs://de_analytics/retail_db/departments/:
gs://de_analytics/retail_db/departments/part-00000

gs://de_analytics/retail_db/order_items/:
gs://de_analytics/retail_db/order_items/part-00000

gs://de_analytics/retail_db/orders/:
gs://de_analytics/retail_db/orders/part-00000

gs://de_analytics/retail_db/products/:
gs://de_analytics/retail_db/products/part-00000

File and folder as objects in bucket (container)

### Create bucket using Command Line Interface (CLI)

