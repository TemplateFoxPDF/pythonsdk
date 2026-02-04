# CreatePdfRequest

Request model for PDF generation

## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**template_id** | **str** | **Required.** Template short ID (12 characters) | 
**data** | **Dict[str, object]** | **Required.** Key-value data to render in the template. Keys must match template variables. | 
**export_type** | [**ExportType**](ExportType.md) | Export format: &#x60;url&#x60; uploads to CDN and returns URL, &#x60;binary&#x60; returns raw PDF bytes | [optional] 
**expiration** | **int** | URL expiration in seconds. Min: 60 (1 min), Max: 604800 (7 days). Only applies to &#x60;url&#x60; export type. | [optional] [default to 86400]
**filename** | **str** |  | [optional] 
**store_s3** | **bool** | Upload to your configured S3 bucket instead of CDN | [optional] [default to False]
**s3_filepath** | **str** |  | [optional] 
**s3_bucket** | **str** |  | [optional] 

## Example

```python
from templatefox.models.create_pdf_request import CreatePdfRequest

# TODO update the JSON string below
json = "{}"
# create an instance of CreatePdfRequest from a JSON string
create_pdf_request_instance = CreatePdfRequest.from_json(json)
# print the JSON string representation of the object
print(CreatePdfRequest.to_json())

# convert the object into a dict
create_pdf_request_dict = create_pdf_request_instance.to_dict()
# create an instance of CreatePdfRequest from a dict
create_pdf_request_from_dict = CreatePdfRequest.from_dict(create_pdf_request_dict)
```
[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)


