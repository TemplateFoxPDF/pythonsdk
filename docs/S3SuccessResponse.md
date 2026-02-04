# S3SuccessResponse

Generic success response for S3 operations

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**success** | **bool** | Whether the operation succeeded | 

## Example

```python
from templatefox.models.s3_success_response import S3SuccessResponse

# TODO update the JSON string below
json = "{}"
# create an instance of S3SuccessResponse from a JSON string
s3_success_response_instance = S3SuccessResponse.from_json(json)
# print the JSON string representation of the object
print(S3SuccessResponse.to_json())

# convert the object into a dict
s3_success_response_dict = s3_success_response_instance.to_dict()
# create an instance of S3SuccessResponse from a dict
s3_success_response_from_dict = S3SuccessResponse.from_dict(s3_success_response_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


