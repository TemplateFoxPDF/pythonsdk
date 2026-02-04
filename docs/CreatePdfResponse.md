# CreatePdfResponse

Response for URL export type

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**url** | **str** | Signed URL to download the PDF (expires after specified time) | 
**filename** | **str** | Filename of the generated PDF | 
**credits_remaining** | **int** | Remaining credits after this request | 
**expires_in** | **int** | Seconds until URL expires | 

## Example

```python
from templatefox.models.create_pdf_response import CreatePdfResponse

# TODO update the JSON string below
json = "{}"
# create an instance of CreatePdfResponse from a JSON string
create_pdf_response_instance = CreatePdfResponse.from_json(json)
# print the JSON string representation of the object
print(CreatePdfResponse.to_json())

# convert the object into a dict
create_pdf_response_dict = create_pdf_response_instance.to_dict()
# create an instance of CreatePdfResponse from a dict
create_pdf_response_from_dict = CreatePdfResponse.from_dict(create_pdf_response_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


