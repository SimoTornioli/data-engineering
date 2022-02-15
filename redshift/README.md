# Sparkify-data-warehouse with Redshift
_____

## Summary

This project is about moving song listen log files with song metadata to a data warehouse to facilitate analytics. Data is read from json files stored in AWS S3 buckets in a parallel manner and uploaded to tables in a Redshift cluster (previously created using the Python SDK). A data pipeline built in Python and SQL prepares a data schema designed for analytics. The JSON data seats in two staging tables before being inserted into a star schema with fact and dimension tables `users`, `songs`, `artists`, and `time`. A star schema is suitable for this application since denormalization is easy, queries can be kept simple, and aggregations are fast. The tables are partitioned using partition and sorting keys in Redshift to improve query time.

## Files

`dwh.cfg` Configure Redshift cluster and data import

`create_tables.py` Drop and recreate tables

`etl.py` Copy data to staging tables and insert into star schema fact and dimension tables

`sql_queries.py`

- Creating and dropping staging and star schema tables
- Copy JSON data from S3 to Redshift staging tables
- Insert data from staging tables to star schema fact and dimension tables

## Run scripts

Set DB/DB_PASSWORD, CLUSTER/HOST, IAM_ROLE/ARN in dhw.cfg.

Drop and recreate tables

    python create_tables.py
Run ETL pipeline

    python etl.py