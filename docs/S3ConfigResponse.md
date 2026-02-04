# S3ConfigResponse

Response for S3 configuration (with masked secret)

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**configured** | **bool** | Whether S3 is configured | 
**endpoint_url** | **str** | S3-compatible endpoint URL | 
**access_key_id** | **str** | Access key ID | 
**secret_access_key_masked** | **str** | Masked secret access key (shows first 4 and last 4 characters) | 
**bucket_name** | **str** | S3 bucket name | 
**default_prefix** | **str** | Default path prefix for uploads | 

## Example

```python
from templatefox.models.s3_config_response import S3ConfigResponse

# TODO update the JSON string below
json = "{}"
# create an instance of S3ConfigResponse from a JSON string
s3_config_response_instance = S3ConfigResponse.from_json(json)
# print the JSON string representation of the object
print(S3ConfigResponse.to_json())

# convert the object into a dict
s3_config_response_dict = s3_config_response_instance.to_dict()
# create an instance of S3ConfigResponse from a dict
s3_config_response_from_dict = S3ConfigResponse.from_dict(s3_config_response_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


