# templatefox.AccountApi

All URIs are relative to *https://api.pdftemplateapi.com*

Method | HTTP request | Description
------------- | ------------- | -------------
[**get_account**](AccountApi.md#get_account) | **GET** /v1/account | Get account info
[**list_transactions**](AccountApi.md#list_transactions) | **GET** /v1/account/transactions | List transactions


# **get_account**
> AccountInfoResponse get_account()

Get account info

Get account information including remaining credits.

**Authentication:** API Key required (`x-api-key` header) or JWT token

**Usage:** Check credit balance before performing operations.

**No credits consumed:** This is a read-only endpoint.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.account_info_response import AccountInfoResponse
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
    api_instance = templatefox.AccountApi(api_client)

    try:
        # Get account info
        api_response = api_instance.get_account()
        print("The response of AccountApi->get_account:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling AccountApi->get_account: %s\n" % e)
```



### Parameters

This endpoint does not need any parameter.

### Return type

[**AccountInfoResponse**](AccountInfoResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Account information |  -  |
**403** | Invalid or missing API key |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

# **list_transactions**
> TransactionsResponse list_transactions(limit=limit, offset=offset)

List transactions

List transaction history for the authenticated user.

**Authentication:** API Key required (`x-api-key` header) or JWT token

**Pagination:** Use `limit` and `offset` query parameters.

**Transaction types:**
- `PDFGEN`: PDF generation (consumes credits)
- `REFUND`: Credit refund (on failed generation)
- `PURCHASE`: Credit purchase
- `BONUS`: Bonus credits

**Credits field:**
- Positive value = credits consumed
- Negative value = credits added

**No credits consumed:** This is a read-only endpoint.

### Example

* Api Key Authentication (ApiKeyAuth):

```python
import templatefox
from templatefox.models.transactions_response import TransactionsResponse
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
    api_instance = templatefox.AccountApi(api_client)
    limit = 300 # int | Number of records to return (optional) (default to 300)
    offset = 0 # int | Number of records to skip (optional) (default to 0)

    try:
        # List transactions
        api_response = api_instance.list_transactions(limit=limit, offset=offset)
        print("The response of AccountApi->list_transactions:\n")
        pprint(api_response)
    except Exception as e:
        print("Exception when calling AccountApi->list_transactions: %s\n" % e)
```



### Parameters


Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **limit** | **int**| Number of records to return | [optional] [default to 300]
 **offset** | **int**| Number of records to skip | [optional] [default to 0]

### Return type

[**TransactionsResponse**](TransactionsResponse.md)

### Authorization

[ApiKeyAuth](../README.md#ApiKeyAuth)

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details

| Status code | Description | Response headers |
|-------------|-------------|------------------|
**200** | Transaction history |  -  |
**403** | Invalid or missing API key |  -  |
**422** | Validation Error |  -  |

[[Back to top]](#) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to Model list]](../README.md#documentation-for-models) [[Back to README]](../README.md)

