# Transaction

Transaction record

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**transaction_ref** | **str** | Unique transaction reference (UUID) | 
**transaction_type** | **str** | Transaction type: PDFGEN, PURCHASE, REFUND, BONUS | 
**template_id** | **str** |  | [optional] 
**exec_tm** | **int** |  | [optional] 
**credits** | **int** | Credits consumed (positive) or added (negative) | 
**created_at** | **str** | ISO 8601 timestamp | 

## Example

```python
from templatefox.models.transaction import Transaction

# TODO update the JSON string below
json = "{}"
# create an instance of Transaction from a JSON string
transaction_instance = Transaction.from_json(json)
# print the JSON string representation of the object
print(Transaction.to_json())

# convert the object into a dict
transaction_dict = transaction_instance.to_dict()
# create an instance of Transaction from a dict
transaction_from_dict = Transaction.from_dict(transaction_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


