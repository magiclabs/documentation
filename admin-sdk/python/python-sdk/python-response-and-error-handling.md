# Response and Error Handling

## Response

There is only one response object that will be returned from a successful API call.

### MagicResponse

This is the interface to interact Magic API responses. It will only be returned if the API request status code is between 200 \(inclusive\) and 300 \(exclusive\).

You will have access to the following attributes:

* `content` \(bytes\): Raw content returned by the API response.
* `status_code` \(num\): HTTP status code for the given request.
* `data` \(dict\): Parsed content.

```python
from magic_admin.response import MagicResponse

MagicResponse.content
MagicResponse.status
MagicResponse.data
```

## Errors

The conventional HTTP response is adopted by the SDK. For the status code in :

* `2XX` - Indicates success
* `4XX` - Indicates client errors. Information provided to the SDK is invalid.
* `5XX` - Indicates server errors

Below is the error class inheritance which can help  developers to programmatically handle the error cases.

```text
MagicError
    |
    |------- DIDTokenError
    |
    |------- RequestError
                  |
                  | ------- RateLimitingError
                  | ------- BadRequestError
                  | ------- AuthenticationError
                  | ------- ForbiddenError
                  | ------- APIError
                  | ------- APIConnectionError
```

### MagicError

This is the base class of all the Magic SDK errors.

```python
MagicError(message=None)
```

### DIDTokenError

Any DID Token related error. This can mean the given token is malformed or invalid.

### RequestError

This is the base class of all the Magic API request errors. This error class will provide details of unsuccessful API requests.

```python
RequestError(
    message=None, http_status=None, http_code=None, http_resp_data=None,
    http_message=None, http_error_code=None, http_request_params=None,
    http_request_data=None, http_method=None,
)
```

#### RateLimitingError

\[**429**\]: Too many requests are submitted for a given period of time.

#### BadRequestError

\[**400**\]:  The API requests might have missing required fields or bad inputs.

#### AuthenticationError

\[**401**\]: This means your API secret key is invalid.

#### ForbiddenError

\[**403**\]: This normally means the given API secret key doesn't have permission to perform the action on the given resources.

#### APIError

This is a generic API error that handlers other status codes that are not explicitly handled. Ex: `500` , `404` , etc.

#### APIConnectionError

Network connection error. This normally means the connection between between your application and Magic API server cannot be established.

### Error Handling

It is recommended to handle the API errors gracefully.

```python
try:
    # Make requests to Magic server.  
except DIDTokenError as e:
    pass
except RateLimitingError as e:
    pass
except BadRequestError as e:
    pass
except AuthenticationError as e:
    pass
except ForbiddenError as e:
    pass
except APIError as e:
    pass
except APIConnectionError as e:
    pass
```

