# Client Sign Up

{% api-method method="post" host="https://api.huygens.com" path="/v1/signup" %}
{% api-method-summary %}
Client Sign Up 
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows client sign up to Huygens Search API. 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
Value: `application/json`
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="--data-raw" type="object" required=true %}
**Client Request** object wrapped in **Request** object
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
On success, the response body contains a **Client Response** object wrapped in **Response** object in JSON. This user code is required to Generate Token.  
  
**Example:**
{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Request" %}
```bash
curl --location --request GET 'https://api.huygens.com/v1/singup' \
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
        "email": "example@huygens.com",
        "password": "HelloW0rld",
        "app_name": "My App",
        "redirect_urls: [
            "http://mysite.com/callback/",
            ...
        ]
    }
}'
```
{% endtab %}

{% tab title="Response" %}
```
{
    "info": {
        "type": "success",
        "title": "Succefull user register",
        "message": "User has been succefull register",
        "code": "0"
    },
    "content": {
        "client_id": "1d4b0fae807b4f2d876...",
        "secret_key": "059bdc1f26314ab395..."
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

### Client Request Object

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
      <td style="text-align:left">email</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">A valid email</td>
    </tr>
    <tr>
      <td style="text-align:left">password</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">
        <p>A valid user password.
          <br />Rules:</p>
        <p><code>6 or more characters</code>
        </p>
        <p><code>Upper &amp; lowercase letter</code>
        </p>
        <p><code>At leas one number</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">app_name</td>
      <td style="text-align:left"><code>String</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">Your app client name</td>
    </tr>
    <tr>
      <td style="text-align:left">redirects_urls</td>
      <td style="text-align:left"><code>Array(String)</code>
      </td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">White-listed addresses to redirect to after authentication success OR
        failure (e.g. <a href="http://mysite.com/callback/">http://mysite.com/callback/</a>)</td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="JSON Example" %}
```text
{
    "email": "example@huygens.com",
    "password": "HelloW0rld",
    "app_name": "My App",
    "redirect_urls: [
        "http://mysite.com/callback/",
        ...
    ]
}
```
{% endtab %}
{% endtabs %}

### Client Response Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| client\_id | `String` | **`Required`** | Client id |
| secret\_key | `String` | **`Required`** | Client secret key |
{% endtab %}

{% tab title="JSON Example" %}
```text
{
     "client_id": "1d4b0fae807b4f2d876...",
     "secret_key": "059bdc1f26314ab395..."
}
```
{% endtab %}
{% endtabs %}

For further information about this flow, see _Client Credentials Grant_ definition in [RFC-6749, section 4.4.](https://tools.ietf.org/html/rfc6749#section-4.4)

