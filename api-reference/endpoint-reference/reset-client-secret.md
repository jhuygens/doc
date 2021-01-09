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
**Request** object
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



