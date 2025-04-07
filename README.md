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
gsutil mb gs://de_analytics

## Copy datasets into the bucket
gsutil cp -r data/retail_db gs://de_analytics/data/retail_db

gsutil ls gs://de_analytics/
gsutil ls -r gs://de_analytics/

## Cleanup the bucket
### empty bucket if the bucket is empty else error:
gsutil rb gs://de_analytics
Removing gs://de_analytics/...
NotEmptyException: 409 BucketNotEmpty (de_analytics)

### all data recursively :
gsutil rb gs://de_analytics
Removing gs://de_analytics/...
NotEmptyException: 409 BucketNotEmpty (de_analytics)
kushwaharitu893@cloudshell:~/gcp-cook-book (spring-base-455810-r1)$ gsutil rm -r gs://de_analytics/data/retail_db
Removing gs://de_analytics/data/retail_db/categories/part-00000#1744016887729993...
Removing gs://de_analytics/data/retail_db/create_db_tables_pg.sql#1744016885568058...
Removing gs://de_analytics/data/retail_db/customers/part-00000#1744016890257527...
Removing gs://de_analytics/data/retail_db/departments/part-00000#1744016890629605...
/ [4 objects]                                                                   
==> NOTE: You are performing a sequence of gsutil operations that may
run significantly faster if you instead use gsutil -m rm ... Please
see the -m section under "gsutil help options" for further information
about when gsutil -m can be advantageous.

Removing gs://de_analytics/data/retail_db/load_db_tables_pg.sql#1744016883893356...
Removing gs://de_analytics/data/retail_db/order_items/part-00000#1744016895974621...
Removing gs://de_analytics/data/retail_db/orders/part-00000#1744016892777887... 
Removing gs://de_analytics/data/retail_db/products/part-00000#1744016887371619...
Removing gs://de_analytics/data/retail_db/schemas.json#1744016885204513...      
/ [9 objects]                                                                   
Operation completed over 9 objects.           

### this will remove bucket as well
gsutil rm -r gs://de_analytics
Removing gs://de_analytics/data/retail_db/categories/part-00000#1744017293784601...
Removing gs://de_analytics/data/retail_db/create_db_tables_pg.sql#1744017292536164...
Removing gs://de_analytics/data/retail_db/customers/part-00000#1744017295380088...
Removing gs://de_analytics/data/retail_db/departments/part-00000#1744017295739320...
/ [4 objects]                                                                   
==> NOTE: You are performing a sequence of gsutil operations that may
run significantly faster if you instead use gsutil -m rm ... Please
see the -m section under "gsutil help options" for further information
about when gsutil -m can be advantageous.

Removing gs://de_analytics/data/retail_db/load_db_tables_pg.sql#1744017291799977...
Removing gs://de_analytics/data/retail_db/order_items/part-00000#1744017300832181...
Removing gs://de_analytics/data/retail_db/orders/part-00000#1744017298599002... 
Removing gs://de_analytics/data/retail_db/products/part-00000#1744017293418878...
Removing gs://de_analytics/data/retail_db/schemas.json#1744017292159362...      
/ [9 objects]                                                                   
Operation completed over 9 objects.                                              
Removing gs://de_analytics/...


## Manage buckets and files in GCS using CLI

## Manage buckets and files in GCS using Python (VS Code)
gcloud 
gcloud info
gsutil
gsutil help 

to check if the python has google clous torage

python
Python 3.9.21 (main, Dec  3 2024, 17:50:13) 
[Clang 16.0.0 (clang-1600.0.26.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from google.cloud import storage
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ModuleNotFoundError: No module named 'google'
>>> exit()

```
pip3 install google-cloud-storage
```
success:
python                           
Python 3.9.21 (main, Dec  3 2024, 17:50:13) 
[Clang 16.0.0 (clang-1600.0.26.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from google.cloud import storage
>>> 

Python Noteboook - Manage Files in GCS using Python.ipynb


For Authentication: gcloud auth application-default login