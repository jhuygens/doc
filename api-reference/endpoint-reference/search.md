---
description: Search service
---

# Search

{% api-method method="get" host="https://api.huygens.com" path="/v1/search" %}
{% api-method-summary %}
Search
{% endapi-method-summary %}

{% api-method-description %}
This endpoint allows you to get catalog information about albums, artists, playlists, tracks, shows, movies, peoples or episodes that match a keyword string.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" required=true %}
A valid access token from the Huygens API: see the Authorization Guide for details.
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="q" required=true type="string" %}
Search query keywords and optional field filters.Valid field filters are: `name, year, country,`   
For example:  
`q=Pinck%20Floyd`
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
A comma-separated list of item types to search across.  
Valid types are: `album , artist, playlist, track, show, movie, people and episode`  
Search results include hits from all the specified item types.  
For example: `q=name:nirvana&type=album,track` returns both albums and tracks with **`nirvana`** included in their name.
{% endapi-method-parameter %}

{% api-method-parameter %}

{% endapi-method-parameter %}

{% api-method-parameter %}

{% endapi-method-parameter %}

{% api-method-parameter %}

{% endapi-method-parameter %}

{% api-method-parameter %}

{% endapi-method-parameter %}

{% api-method-parameter name="gluten" type="boolean" %}
Whether the cake should be gluten-free or not.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
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



