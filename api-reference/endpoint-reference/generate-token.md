# Generate Token

{% api-method method="post" host="https://api.huygens.com" path="/v1/token" %}
{% api-method-summary %}
Generate Token
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
**Generate Token Request** object wrapped in **Request** JSON object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{    "name": "Cake's name",    "recipe": "Cake's recipe name",    "cake": "Binary cake"}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```
{    "message": "Ain't no cake like that."}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Generate Token Request Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| grant\_type | `String` | **`Required`** | As defined in the OAuth 2.0 specification, this field must contain the value `"authorization_code"`. |
| code | `String` | **`Required`** | The authorization code returned from the request to the Sing Up endpoint: `/v1/singup` |
| username | `String` | **`Required`** | Registered username. |
{% endtab %}

{% tab title="JSON" %}
```text
{
    "garant_type": "authorization_code",
    "code": "24HLJ123",
    "username" "example"
}
```
{% endtab %}
{% endtabs %}

### Token

Is a `JSON string` param, this is an encode Token based in [Bearer Authentication](https://tools.ietf.org/html/rfc6750).





