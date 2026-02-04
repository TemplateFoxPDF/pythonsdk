# templatefox.TemplatesApi

All URIs are relative to *https://api.pdftemplateapi.com*

Method | HTTP request | Description
------------- | ------------- | -------------
[**get_template_fields**](TemplatesApi.md#get_template_fields) | **GET** /v1/templates/{template_id}/fields | Get template fields
[**list_templates**](TemplatesApi.md#list_templates) | **GET** /v1/templates | List templates


# **get_template_fields**
> List[TemplateField] get_template_fields(template_id)

Get template fields

Get the dynamic fields for a template.

**Authentication:** API Key required (`x-api-key` header) or JWT token

**Usage:** This endpoint is designed for Zapier Dynamic Fields integration.
It returns an array of field definitions that Zapier uses to dynamically
generate input forms.

**Response format:** Array of objects compatible with Zapier InputFieldsSchema.
Each field has: `key`, `label`, `type`, `required`, and optional `helpText`.

**Field types:**
- `string`: Text input (also used for JSON arrays/objects)
- `integer`: Integer number
- `number`: Decimal number
- `boolean`: True/False checkbox

**Arrays and objects:** Complex types are returned as `string` type with
a `helpText` showing the expected JSON format.

**No credits consumed:** This is a read-only endpoint.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.template_field import TemplateField
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
    api_instance = templatefox.TemplatesApi(api_client)
    template_id = 'template_id_example' # str | 

    try:
        # Get template fields
        api_response = api_instance.get_template_fields(template_id)
        print("The response of TemplatesApi->get_template_fields:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling TemplatesApi->get_template_fields: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **template_id** | **str**|  | 

### Return type

[**List[TemplateField]**](TemplateField.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | List of template fields |  -  |
**403** | Invalid or missing API key |  -  |
**404** | Template not found |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_templates**
> TemplatesListResponse list_templates()

List templates

List all templates for the authenticated user.

**Authentication:** API Key required (`x-api-key` header) or JWT token

**Usage:** This endpoint is designed for no-code tools (Zapier, Make, n8n) to populate
template selection dropdowns.

**No credits consumed:** This is a read-only endpoint.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.templates_list_response import TemplatesListResponse
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
    api_instance = templatefox.TemplatesApi(api_client)

    try:
        # List templates
        api_response = api_instance.list_templates()
        print("The response of TemplatesApi->list_templates:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling TemplatesApi->list_templates: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

[**TemplatesListResponse**](TemplatesListResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | List of templates |  -  |
**403** | Invalid or missing API key |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

