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
| user\_code | `String` | **`Required`** | User code generate in **Sing Up** service |
| email | `String` | **`Required`** | User email |
| password | `String` | **`Required`** | Valid user password  |
{% endtab %}

{% tab title="JSON" %}
```text
{
    "user_code": "24HLJ123",
    "email": "example@huygens.com",
    "password" "HelloW0rld"
}
```
{% endtab %}
{% endtabs %}

