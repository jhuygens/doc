---
description: 'The request is sent to the /v1/token endpoint of the Auth service:'
---

# 1. Have your application request authorization

{% api-method method="post" host="https://api.huygens.com" path="/v1/token" %}
{% api-method-summary %}
Access Token
{% endapi-method-summary %}

{% api-method-description %}
The body of this POST request must contain the following parameters encoded in `application/x-www-form-urlencoded` as defined in the **OAuth 2.0** specification:
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Base 64 encoded string that contains the client ID and client secret key. The field must have the format: Authorization: `Basic <base64 encoded client_id:client_secret>`
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
Value: `application/x-www-form-urlencoded`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="grant\_type" type="object" required=true %}
Set it to `client_credentials`
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
--header 'Content-Type: application/x-www-form-urlencoded' \
--data-urlencode 'grant_type=client_credentials'
```
{% endtab %}

{% tab title="Response" %}
```
{
     "access_token": "NgCXRKc...MzYjw",
     "token_type": "bearer",
     "expires_in": 3600
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

### Access Token Response Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| access\_token | `String` | **`Required`** | An access token that can be provided in subsequent calls to API services. |
| token\_type | `String` | **`Required`** | How the access token may be used: always “Bearer”. |
| expires\_in | `Integer` | **`Required`** | The time period \(in seconds\) for which the access token is valid. |
{% endtab %}

{% tab title="JSON Example" %}
```text
{
   "access_token": "NgCXRK...MzYjw",
   "token_type": "Bearer",
   "expires_in": 3600
}
```
{% endtab %}
{% endtabs %}

For more information view [OAuth 2.0](https://tools.ietf.org/html/rfc6749) specifications.

### Access Token Request Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| grant\_type | `String` | **`Required`** | As defined in the OAuth 2.0 specification, this field must contain the value `"authorization_code" or "refresh_token"` |
| code | `String` | `Optional` | The authorization code returned from the request to the Sing Up endpoint: `/v1/singup` |
| username | `String` | `Optional` | Registered username. |
| refresh\_token | `String` | `Optional` | The refresh token returned from the authorization code exchange. |
{% endtab %}

{% tab title="JSON Example" %}
```text
{
    "garant_type": "authorization_code",
    "code": "24HLJ123",
    "username": "example",
    "refresh_token": "NgAagA...NUm_SHo"
}
```
{% endtab %}
{% endtabs %}





