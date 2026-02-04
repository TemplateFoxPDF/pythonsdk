# templatefox.IntegrationsApi

All URIs are relative to *https://api.pdftemplateapi.com*

Method | HTTP request | Description
------------- | ------------- | -------------
[**delete_s3_config**](IntegrationsApi.md#delete_s3_config) | **DELETE** /v1/integrations/s3 | Delete S3 configuration
[**get_s3_config**](IntegrationsApi.md#get_s3_config) | **GET** /v1/integrations/s3 | Get S3 configuration
[**save_s3_config**](IntegrationsApi.md#save_s3_config) | **POST** /v1/integrations/s3 | Save S3 configuration
[**test_s3_connection**](IntegrationsApi.md#test_s3_connection) | **POST** /v1/integrations/s3/test | Test S3 connection


# **delete_s3_config**
> S3SuccessResponse delete_s3_config()

Delete S3 configuration

Delete S3 storage configuration.

**Authentication:** API Key required (`x-api-key` header) with admin privileges

**Usage:** Remove your S3 integration. Generated PDFs will use the default CDN storage after deletion.

**Warning:** This action is irreversible. You'll need to reconfigure S3 to use it again.

**No credits consumed:** This is a configuration endpoint.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.s3_success_response import S3SuccessResponse
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
    api_instance = templatefox.IntegrationsApi(api_client)

    try:
        # Delete S3 configuration
        api_response = api_instance.delete_s3_config()
        print("The response of IntegrationsApi->delete_s3_config:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->delete_s3_config: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

[**S3SuccessResponse**](S3SuccessResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Configuration deleted successfully |  -  |
**403** | Admin privileges required |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **get_s3_config**
> S3ConfigResponse get_s3_config()

Get S3 configuration

Get current S3 storage configuration.

**Authentication:** API Key required (`x-api-key` header) with admin privileges

**Usage:** Retrieve your S3 integration settings. Secret access key is masked for security.

**Returns 404** if S3 is not configured.

**No credits consumed:** This is a read-only endpoint.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.s3_config_response import S3ConfigResponse
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
    api_instance = templatefox.IntegrationsApi(api_client)

    try:
        # Get S3 configuration
        api_response = api_instance.get_s3_config()
        print("The response of IntegrationsApi->get_s3_config:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->get_s3_config: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

[**S3ConfigResponse**](S3ConfigResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | S3 configuration retrieved successfully |  -  |
**403** | Admin privileges required |  -  |
**404** | S3 is not configured |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **save_s3_config**
> S3SuccessResponse save_s3_config(s3_config_request)

Save S3 configuration

Save or update S3-compatible storage configuration.

**Authentication:** API Key required (`x-api-key` header) with admin privileges

**Usage:** Configure your S3-compatible storage to receive generated PDFs directly
in your own bucket instead of the default CDN.

**Supported providers:**
- Amazon S3
- DigitalOcean Spaces
- Cloudflare R2
- MinIO
- Any S3-compatible storage

**Secret key behavior:**
- For new configuration: `secret_access_key` is required
- For updates: Omit `secret_access_key` to keep existing value

**No credits consumed:** This is a configuration endpoint.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.s3_config_request import S3ConfigRequest
from templatefox.models.s3_success_response import S3SuccessResponse
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
    api_instance = templatefox.IntegrationsApi(api_client)
    s3_config_request = templatefox.S3ConfigRequest() # S3ConfigRequest | 

    try:
        # Save S3 configuration
        api_response = api_instance.save_s3_config(s3_config_request)
        print("The response of IntegrationsApi->save_s3_config:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->save_s3_config: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **s3_config_request** | [**S3ConfigRequest**](S3ConfigRequest.md)|  | 

### Return type

[**S3SuccessResponse**](S3SuccessResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Configuration saved successfully |  -  |
**400** | Invalid configuration (e.g., missing secret key for new config) |  -  |
**403** | Admin privileges required |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **test_s3_connection**
> S3TestResponse test_s3_connection()

Test S3 connection

Test S3 connection with stored credentials.

**Authentication:** API Key required (`x-api-key` header) with admin privileges

**Usage:** Verify your S3 configuration is working correctly. The test will:
1. Connect to the endpoint
2. Verify bucket access
3. Check write permissions by uploading a small test file

**Prerequisite:** S3 must be configured first using `POST /v1/integrations/s3`

**No credits consumed:** This is a diagnostic endpoint.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.s3_test_response import S3TestResponse
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
    api_instance = templatefox.IntegrationsApi(api_client)

    try:
        # Test S3 connection
        api_response = api_instance.test_s3_connection()
        print("The response of IntegrationsApi->test_s3_connection:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling IntegrationsApi->test_s3_connection: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

[**S3TestResponse**](S3TestResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Connection test successful |  -  |
**400** | Connection test failed |  -  |
**403** | Admin privileges required |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

