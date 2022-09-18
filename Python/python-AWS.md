<h1>Python & AWS</h1>


```python
AWS_S3_BUCKET = os.getenv("backet_name")
AWS_ACCESS_KEY_ID = os.getenv("AWS_ACCESS_KEY_ID")
AWS_SECRET_ACCESS_KEY = os.getenv("AWS_SECRET_ACCESS_KEY")
key = "key/"
```
1. Read data from S3:
```python
df = pd.read_parquet(
    f"s3://{backet_name}/{key}"+"<file_name>.parquet/",
    storage_options={
        "key": AWS_ACCESS_KEY_ID,
        "secret": AWS_SECRET_ACCESS_KEY,
    })
```
2. Write data to S3:
```python
df.to_csv(
    f"s3://{backet_name}/{key}"+"data/",
    index=False,
    storage_options={
        "key": AWS_ACCESS_KEY_ID,
        "secret": AWS_SECRET_ACCESS_KEY,
    })
```
3.