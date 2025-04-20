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


# ☁️ GCP Cloud SQL with PostgreSQL
This demonstrates how to set up and manage a PostgreSQL instance on Google Cloud SQL, connect to it locally or via a client, and perform basic database operations using the command line and Python.

## 📖 Overview
Google Cloud SQL is a fully-managed relational database service for MySQL, PostgreSQL, and SQL Server. This guide focuses on using PostgreSQL with GCP Cloud SQL for applications that require scalability, reliability, and high availability.

## ✅ Prerequisites

### Install Google Cloud SDK
https://cloud.google.com/sdk/docs/install

### Authenticate GCP
gcloud auth login

### Set project
gcloud config set project YOUR_PROJECT_ID
🏗️ Create Cloud SQL PostgreSQL Instance

gcloud sql instances create pg-demo-instance \
    --database-version=POSTGRES_13 \
    --cpu=1 \
    --memory=4GB \
    --region=us-central1

Check with telnet the public IP of instance or Outgoing IP address
If not add your IP in Connection

### Set a password for the default user 'postgres'
gcloud sql users set-password postgres \
    --instance=pg-demo-instance \
    --password=YOUR_PASSWORD

## 🔌 Connect to Cloud SQL
* Via Cloud Shell (Recommended)
```
gcloud sql connect pg-demo-instance --user=postgres
```
* Via Public IP (Enable Public IP):
```
gcloud sql instances patch pg-demo-instance --assign-ip
```
* Add your IP to authorized networks:
```
gcloud sql instances patch pg-demo-instance \
    --authorized-networks="$(curl ifconfig.me)/32"
```

##Connect using a PostgreSQL client:
```
psql "host=INSTANCE_IP dbname=postgres user=postgres password=YOUR_PASSWORD"
```
### 🧱 Create Database and Tables
```
-- Create a new database
CREATE DATABASE customer_data;

-- Switch to the new DB
\c customer_data

-- Create a sample table
CREATE TABLE customers (
  id SERIAL PRIMARY KEY,
  name TEXT NOT NULL,
  email TEXT UNIQUE NOT NULL
);

-- Insert sample data
INSERT INTO customers (name, email)
VALUES ('Alice', 'alice@example.com'),
       ('Bob', 'bob@example.com');
```

### 🐍 Python Integration
```
import psycopg2

conn = psycopg2.connect(
    host='INSTANCE_IP',
    database='customer_data',
    user='postgres',
    password='YOUR_PASSWORD'
)

cur = conn.cursor()
cur.execute("SELECT * FROM customers;")
rows = cur.fetchall()

for row in rows:
    print(row)

conn.close()
```

## 💾 Backup and Restore

### Export backup
```
gcloud sql export sql pg-demo-instance gs://your-bucket-name/backup.sql.gz \
    --database=customer_data
```

### Import backup
```
gcloud sql import sql pg-demo-instance gs://your-bucket-name/backup.sql.gz \
    --database=customer_data
```

## 🛡️ Best Practices
* 🔐 Use private IP for secure networking (VPC)
* 🔄 Enable automated backups and point-in-time recovery
* 🧪 Set up replicas for HA or read scaling
* 🧮 Enable Query Insights for performance monitoring
* 🔒 Use IAM and SSL for connection security

## 🧹 Cleanup
### Delete instance
```
gcloud sql instances delete pg-demo-instance
```

### Optionally delete storage bucket
```
gsutil rm -r gs://your-bucket-name/
```

### 📚 Resources
Cloud SQL Docs (PostgreSQL)
psycopg2 Python Library
Google Cloud IAM
