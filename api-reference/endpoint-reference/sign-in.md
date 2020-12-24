# Sign In

{% api-method method="post" host="https://api.cakes.com" path="/v1/signin" %}
{% api-method-summary %}
Sign In
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
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
Credentials object wrapped in Request object
{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
On success, the response body contains a **User Code** wrapped in **Response** object in JSON. This user code is required to Generate Token.
{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Request" %}
```bash
curl --location --request GET 'https://api.cakes.com/v1/singin' \
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
        "password": "example",
        "username": "example" 
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
        "user_code": "q1L4JK2"
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

### Credentials Object

|  |  |
| :--- | :--- |
|  |  |

### User Code

Is a JSON string param, this user code is required to [Generate Token](generate-token.md#generate-token). To retrieve the user code use the recover user code service.

