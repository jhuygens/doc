# Reset Client Secret

{% api-method method="get" host="https://api.cakes.com" path="/v1/reset\_secret" %}
{% api-method-summary %}
Reset Client Secret
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows reset client secret key.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Content-Type" type="string" required=true %}
Value `application/json`
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" required=true type="string" %}
A valid Bearer Authentication Token from the Huygens API: see the **Authorization Guide** for details.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="--data-raw" type="string" required=true %}
**Reset Client Secret Request** object wrapped in a **Request** object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Request" %}
```http
{
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
        "client_id": "1d4b0fae807b4f2d876...",
        "secret_key": "059bdc1f26314ab395...",
        "password": "example", 
    }
}
```
{% endtab %}

{% tab title="Response" %}
```
{
    "info": {
        "type": "error",
        "title": "Error in procces",
        "message": "Error message",
        "code": "1"
    }
    "content": {
        "client_id": "1d4b0fae807b4f2d876...",
        "secret_key": "93g9480940986314ab..."
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
{% endapi-method-response-example-description %}

```
{
    "info": {
        "type": "error",
        "title": "Error in procces",
        "message": "Error message",
        "code": "1"
    }
    "content": nil
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

### Reset Client Secret Request Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| client\_id | `String` | **`Required`** | Client register Id |
| secret\_key | `String` | **`Required`** | Active secret key |
| password | `String` | **`Required`** | Client password |
{% endtab %}

{% tab title="JSON Example" %}
```text
{
     "client_id": "1d4b0fae807b4f2d876...",
     "secret_key": "059bdc1f26314ab395...",
     "password": "example", 
}
```
{% endtab %}
{% endtabs %}

### Reset Client Secret Response Object

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
     "secret_key": "93g9480940986314ab..."
}
```
{% endtab %}
{% endtabs %}



