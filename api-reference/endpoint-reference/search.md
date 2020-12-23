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
Search query keywords and optional field filters.Valid field filters are: `name, year and country`   
For example: `q=name:Pinck%20Floyd`
{% endapi-method-parameter %}

{% api-method-parameter name="type" type="string" required=true %}
A comma-separated list of item types to search across.  
Valid types are: `album , artist, playlist, track, show, movie, podcast, people and episode`  
Search results include hits from all the specified item types.  
For example: `q=name:nirvana&type=album,track` returns both albums and tracks with **`nirvana`** included in their name.
{% endapi-method-parameter %}

{% api-method-parameter name="library" type="string" %}
Services where the API will obtain the information.  
Valid: `itunes, tvmaze and crcind`  
Default: `all`
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="integer" %}
Maximum number of results to return.  
Default: `20`  
Minimun: `1`  
Maximun: `50`  
Note: The limit is applied within each library, not on the total response.  
For example, if the limit value is 3 and the library is `itunes,tvmaze`, the response contains 3 from `itunes` and 3 from `tvmaze`.
{% endapi-method-parameter %}

{% api-method-parameter name="offset" type="integer" %}
The index of the first result to return.  
Default: `0`  
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="integer" %}
Index page.  
Default: `0`
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



