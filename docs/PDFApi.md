# templatefox.PDFApi

All URIs are relative to *https://api.pdftemplateapi.com*

Method | HTTP request | Description
------------- | ------------- | -------------
[**create_pdf**](PDFApi.md#create_pdf) | **POST** /v1/pdf/create | Generate PDF from template


# **create_pdf**
> CreatePdfResponse create_pdf(create_pdf_request)

Generate PDF from template

Generate a PDF from a saved template with dynamic data.

**Authentication:** API Key required (`x-api-key` header)

## Request Body

| Field | Type | Required | Description |
|-------|------|----------|-------------|
| `template_id` | string | ✅ Yes | Template short ID (12 characters) |
| `data` | object | ✅ Yes | Key-value data to render in template |
| `export_type` | string | No | `url` (default) or `binary` |
| `expiration` | integer | No | URL expiration in seconds (60-604800, default: 86400) |

## Export Types
- `url` (default): PDF is uploaded to CDN, returns JSON with URL
- `binary`: Returns raw PDF bytes directly

**Credits:** 1 credit deducted per successful generation.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.create_pdf_request import CreatePdfRequest
from templatefox.models.create_pdf_response import CreatePdfResponse
from templatefox.rest import ApiException
from pprint import pprint

# Defining the host is optional and defaults to https://api.pdftemplateapi.com
# See configuration.py for a list of all supported configuration parameters.
configuration = templatefox.Configuration(
    host = "https://api.pdftemplateapi.com"
)

# The client must configure the authentication and authorization parameters
# in accordance with the API server security policy.
# Examples for each auth method are provided below, use the example that
# satisfies your auth use case.

# Configure API key authorization: ApiKeyAuth
configuration.api_key['ApiKeyAuth'] = os.environ["API_KEY"]

# Uncomment below to setup prefix (e.g. Bearer) for API key, if needed
# configuration.api_key_prefix['ApiKeyAuth'] = 'Bearer'

# Enter a context with an instance of the API client
with templatefox.ApiClient(configuration) as api_client:
    # Create an instance of the API class
    api_instance = templatefox.PDFApi(api_client)
    create_pdf_request = templatefox.CreatePdfRequest() # CreatePdfRequest | 

    try:
        # Generate PDF from template
        api_response = api_instance.create_pdf(create_pdf_request)
        print("The response of PDFApi->create_pdf:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling PDFApi->create_pdf: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **create_pdf_request** | [**CreatePdfRequest**](CreatePdfRequest.md)|  | 

### Return type

[**CreatePdfResponse**](CreatePdfResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json, application/pdf

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | PDF generated successfully |  -  |
**402** | Insufficient credits |  -  |
**403** | Access denied - not your template |  -  |
**404** | Template not found |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

