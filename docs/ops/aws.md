# AWS

## Load JSON file from S3

```python
import json
import boto3

s3_client = boto3.client('s3')

def get_json_data(s3_client: object, bucket: str, key: str) -> dict or None:
    try:
        obj = s3_client.get_object(Bucket=bucket, Key=key)
        return json.loads(obj.get('Body').read())
    except ClientError as e:
        if e.response['Error']['Code'] == 'NoSuchKey':
            return None
        else:
            raise ValueError(e)
```