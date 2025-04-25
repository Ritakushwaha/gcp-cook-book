# 🧰 GCS (Google Cloud Storage) with CLI
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


