# Generate Token

{% api-method method="post" host="https://api.huygens.com" path="/v1/token" %}
{% api-method-summary %}
Generate Token
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get free cakes.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="recipe" type="string" %}
The API will do its best to find a cake matching the provided recipe.
{% endapi-method-parameter %}

{% api-method-parameter name="gluten" type="boolean" %}
Whether the cake should be gluten-free or not.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-form-data-parameters %}
{% api-method-parameter name="" type="object" required=false %}

{% endapi-method-parameter %}
{% endapi-method-form-data-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="" type="object" required=true %}

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



