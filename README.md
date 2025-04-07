# gcp-cook-book
A step-by-step guide to get started with Google Cloud Platform (GCP) for Data Engineering using Python and the command-line interface. This repository helps you learn how to manage data files and buckets using both the gsutil command-line tool and Python SDK.

## 📋 Prerequisites
Before starting, ensure you have the following skills:
✅ SQL: Comfortable querying data using SQL.
✅ Python: Hands-on experience with Python programming.
✅ Data Engineering or Data Warehousing knowledge.
✅ Command Line Basics: Familiarity with terminal tools like bash, zsh, etc.

## 🚀 Getting Started
### 🔐 Sign Up for GCP
* Visit https://cloud.google.com.
* Sign up with a valid email ID.
* New users get $300 credit valid for 3 months.

## 🐍 Python Environment Setup
Ensure Python 3.9 is installed.
```
python3.9 --version
```

### 📦 Create and Activate a Virtual Environment
```
python3.9 -m venv de_env
source de_env/bin/activate
```

### 📥 Install Required Packages
```
pip install <package-name>
```
To save all installed packages:
```
pip freeze > requirements.txt
```
To install packages from an existing file:
```
pip install -r requirements.txt
```

## ☁️ Google Cloud SDK Setup
Click [here](https://cloud.google.com/sdk/docs/install) to go to the instructions related to setting up gcloud CLI.

### Once installed, verify:
```
gcloud info
```
### Authenticate your CLI:
```
gcloud auth login
```
### For Python API authentication:
```
gcloud auth application-default login
```

## 🧰 GCS (Google Cloud Storage) with CLI
### 🔍 List Buckets and Files
```
gsutil ls
gsutil ls gs://de_analytics/
gsutil ls -r gs://de_analytics/
```
### 📦 Example File Structure
```
gs://de_analytics/retail_db/
├── create_db_tables_pg.sql
├── load_db_tables_pg.sql
├── schemas.json
├── categories/
│   └── part-00000
├── customers/
│   └── part-00000
... (other folders)
```

## 🪣 Create a Bucket 
```
gsutil mb gs://de_analytics
```

## 📤 Copy Datasets into Bucket 
gsutil cp -r data/retail_db gs://de_analytics/data/retail_db

## 🧹 Cleanup the Bucket
### Option 1: Remove Specific Data
```
gsutil rm -r gs://de_analytics/data/retail_db
```

### Option 2: Remove Entire Bucket
gsutil rm -r gs://de_analytics

## 🐍 Manage GCS Buckets with Python
### Step 1: Install GCS Client Library
```
pip3 install google-cloud-storage
```
### Step 2: Verify Installation
```
from google.cloud import storage
```

### Refer Notebook : GCS with Python.ipynb

## ✅ Summary

| Task                     | Tool   | Command                                     |
|--------------------------|--------|---------------------------------------------|
| Create bucket            | gsutil | `gsutil mb gs://your-bucket-name`           |
| Upload folder to bucket  | gsutil | `gsutil cp -r local_dir gs://bucket/`       |
| List buckets/files       | gsutil | `gsutil ls` or `gsutil ls -r`               |
| Remove files             | gsutil | `gsutil rm -r gs://bucket/path`             |
| Authenticate CLI         | gcloud | `gcloud auth login`                         |
| Python GCS SDK           | pip    | `pip install google-cloud-storage`          |
