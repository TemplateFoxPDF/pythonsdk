# S3TestResponse

Response for S3 connection test

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**success** | **bool** | Whether the connection test succeeded | 
**message** | **str** | Test result message | 

## Example

```python
from templatefox.models.s3_test_response import S3TestResponse

# TODO update the JSON string below
json = "{}"
# create an instance of S3TestResponse from a JSON string
s3_test_response_instance = S3TestResponse.from_json(json)
# print the JSON string representation of the object
print(S3TestResponse.to_json())

# convert the object into a dict
s3_test_response_dict = s3_test_response_instance.to_dict()
# create an instance of S3TestResponse from a dict
s3_test_response_from_dict = S3TestResponse.from_dict(s3_test_response_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


