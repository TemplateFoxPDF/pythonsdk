# S3ConfigRequest

Request model for S3 configuration

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**endpoint_url** | **str** | S3-compatible endpoint URL. Must start with https:// | 
**access_key_id** | **str** | Access key ID for S3 authentication | 
**secret_access_key** | **str** |  | [optional] 
**bucket_name** | **str** | S3 bucket name. Must follow S3 naming conventions (lowercase, no underscores) | 
**default_prefix** | **str** | Default path prefix for uploaded files. Can include slashes for folder structure | [optional] [default to '']

## Example

```python
from templatefox.models.s3_config_request import S3ConfigRequest

# TODO update the JSON string below
json = "{}"
# create an instance of S3ConfigRequest from a JSON string
s3_config_request_instance = S3ConfigRequest.from_json(json)
# print the JSON string representation of the object
print(S3ConfigRequest.to_json())

# convert the object into a dict
s3_config_request_dict = s3_config_request_instance.to_dict()
# create an instance of S3ConfigRequest from a dict
s3_config_request_from_dict = S3ConfigRequest.from_dict(s3_config_request_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


