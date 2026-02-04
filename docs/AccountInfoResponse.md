# AccountInfoResponse

Response for account info endpoint

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**credits** | **int** | Remaining credits | 
**email** | **str** |  | [optional] 

## Example

```python
from templatefox.models.account_info_response import AccountInfoResponse

# TODO update the JSON string below
json = "{}"
# create an instance of AccountInfoResponse from a JSON string
account_info_response_instance = AccountInfoResponse.from_json(json)
# print the JSON string representation of the object
print(AccountInfoResponse.to_json())

# convert the object into a dict
account_info_response_dict = account_info_response_instance.to_dict()
# create an instance of AccountInfoResponse from a dict
account_info_response_from_dict = AccountInfoResponse.from_dict(account_info_response_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


