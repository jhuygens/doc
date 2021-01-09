# Access Token

{% api-method method="post" host="https://api.huygens.com" path="/v1/token" %}
{% api-method-summary %}
Access Token
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to generate a valid authentication token to made requests in API. This API use **Bearer Authentication**.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true type="string" %}
Base 64 encoded string that contains the client ID and client secret key. The field must have the format: **`Authorization: Basic *<base64 encoded email:password>*`**
{% endapi-method-parameter %}

{% api-method-parameter name="Content-Type" type="string" required=true %}
Value: `application/json`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="--data-raw" type="object" required=true %}
**Access Token Request** object wrapped in **Request** JSON object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
On success, the response body contains an **Access Token Response** object wrapped in Response object in JSON.   
  
**Example:**
{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Request" %}
```bash
curl --location --request GET 'https://api.huygens.com/v1/token' \
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
        {
            "garant_type": "authorization_code",
            "code": "24HLJ123",
            "username": "example",
            "refresh_token": "NgAagA...NUm_SHo"
        }
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
        {
           "access_token": "NgCXRK...MzYjw",
           "token_type": "Bearer",
           "scope": "user-search-resources",
           "expires_in": 3600,
           "refresh_token": "NgAagA...Um_SHo"
        }
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

### Access Token Response Object

{% tabs %}
{% tab title="Definition" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">KEY</th>
      <th style="text-align:left">TYPE</th>
      <th style="text-align:left">RULE</th>
      <th style="text-align:left">VALUE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">access_token</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">An access token that can be provided in subsequent calls to API services.</td>
    </tr>
    <tr>
      <td style="text-align:left">token_type</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">How the access token may be used: always &#x201C;Bearer&#x201D;.</td>
    </tr>
    <tr>
      <td style="text-align:left">scope</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">
        <p>A space-separated list of scopes which have been granted for this <code>access_token</code>
        </p>
        <p>Example: <code>user-search-resources</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">expires_in</td>
      <td style="text-align:left"><code>Integer</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">The time period (in seconds) for which the access token is valid.</td>
    </tr>
    <tr>
      <td style="text-align:left">refresh_token</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">A token that can be sent to the Spotify Accounts service in place of an
        authorization code. (When the access code expires, send a POST request
        to the Accounts service <code>/v1/token</code> endpoint, but use this code
        in place of an authorization code. A new access token will be returned.
        A new refresh token might be returned too.)</td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="JSON Example" %}
```text
{
   "access_token": "NgCXRK...MzYjw",
   "token_type": "Bearer",
   "scope": "user-search-resources",
   "expires_in": 3600,
   "refresh_token": "NgAagA...Um_SHo"
}
```
{% endtab %}
{% endtabs %}

For more information view [OAuth 2.0](https://tools.ietf.org/html/rfc6749) and [OAuth 2.0 Bearer Token Usage ](https://tools.ietf.org/html/rfc6750)specifications.





