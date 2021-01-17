---
description: 'The request is sent to the /v1/token endpoint of the Auth service:'
---

# 1. Have your application request authorization

{% api-method method="post" host="https://api.huygens.com" path="/v1/token" %}
{% api-method-summary %}
Access Token
{% endapi-method-summary %}

{% api-method-description %}
The client can request an access token using only its client credentials.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Base 64 encoded string that contains the client ID and client secret key. The field must have the format: Authorization: `Basic <base64 encoded client_id:client_secret>`
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
Value: `application/json`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="--data-raw" required=true type="string" %}
**Access Token Request** object wrapped in **Request** JSON object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
On success, the response body contains an **Access Token Response** object.  
**Example:**
{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Request" %}
```bash
curl --location --request POST 'https://api.huygens.com/v1/token' \
--header 'Authorization: Basic Y2x1YkJJdiQzcjpiaVA0c3N2djByZA==' \
--header 'Content-Type: application/json' \
--data-raw '{
    "info": {
        "uuid": "23DAFA-ASDFF-A13434..",
        "device": "web",
        "os": "iOS",
        "os_version": "1.0.0",
        "timezone": "UTC-6",
        "lang": "en",
        "app_version": "1.0.0",
        "app_name": "Example App"
    },
    "content": {
        "garant_type": "client_credentials"
    }
}'
```
{% endtab %}

{% tab title="Response" %}
```
{
    "info": {
        "type": "success",
        "title": "Succefull response",
        "message": "",
        "code": "0"
    },
    "content": {
         "access_token": "NgCXRKc...MzYjw",
         "token_type": "bearer",
         "expires_in": 3600
    }
}
```
{% endtab %}
{% endtabs %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The header status code is an error code.  
The response body contains a **Response** object whit error information and error code.  
  
**Example:**
{% endapi-method-response-example-description %}

```
{
    "info": {
        "type": "error",
        "title": "Error in register",
        "message": "User not has been register",
        "code": "1"
    }
    "content": nil
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Access Token Request Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| grant\_type | `String` | **`Required`** | Set it to `client_credentials` |
{% endtab %}

{% tab title="JSON Example" %}
```text
{
    "garant_type": "authorization_code",
}
```
{% endtab %}
{% endtabs %}

### Access Token Response Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| access\_token | `String` | **`Required`** | An access token that can be provided in subsequent calls to API services. |
| token\_type | `String` | **`Required`** | How the access token may be used: always “Bearer”. |
| expires\_in | `Intege` | **`Required`** | The time period \(in seconds\) for which the access token is valid. |
| refresh\_token | `String` | **`Required`** | A token that can be sent to the Huygens Auth service in place of an authorization code. |
{% endtab %}

{% tab title="JSON Example" %}
```text
{
   "access_token": "NgCXRK...MzYjw",
   "token_type": "Bearer",
   "expires_in": 3600,
   "refresh_token": "PoO04alC_uRJoyd2ML...9fKyMaP6zl6g"
}
```
{% endtab %}
{% endtabs %}

For further information about this, see [OAuth 2.0](https://tools.ietf.org/html/rfc6749) specifications.

