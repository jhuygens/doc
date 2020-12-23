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
Search query keywords and optional field filters and operators. Valid field filters are: `name, year and country`   
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
On success, the response body contains an Item object wrapped in a paging object in JSON.  
  
**Example**:
{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Request" %}
```php
curl --location --request GET 'https://api.huygens.com/v1/search?q=name:Pink%20Floyd&type=artist,song&limit=3' \
--header 'Authorization: Basic Y2x1YkJJdiQzcjpiaVA0c3N2djByZA=='
```
{% endtab %}

{% tab title="Response" %}
```go
{
    "info": {
        "type": "success",
        "title": "Succefull response",
        "message": "",
        "code": "0"
    },
    "content": {
        "href": "https://api.huygens.com/v1/search?query=Muse&type=track&market=US&offset=10&limit=10",
        "items":[
            {
                "type": "song",
                "library": "itunes",
                "name": "G's Up (feat. Max B)",
                "artwork_url": "https://audio-ssl.itunes.apple.com/itunes-assets/Music/v4/ff/65/2f/ff652f2b-c347-ef2f-7e86-3c0c32f11dcd/mzaf_5935542688038353189.plus.aac.p.m4a",
                "info": {
                    "preview_url": "https://audio-ssl.itunes.apple.com/itunes-assets/Music/v4/ff/65/2f/ff652f2b-c347-ef2f-7e86-3c0c32f11dcd/mzaf_5935542688038353189.plus.aac.p.m4a",
                    "title": "G's Up (feat. Max B)",
                    "collection": "Harlem: Diary of a Summer",
                    "artist": "Jim Jones",
                    "languages": [
                        "EN",
                        "ES"
                        ],
                    "rating": 7.5,
                    "genres": [
                        "soul", 
                        "hip/hop"
                        ],
                    "description": "",
                    "more_info":"",
                    "release_date": "2005-08-23",
                    "country": "US",
                    "price": 2.9,
                    "rental_price": 0.99,
                    "currency": "USD",
                    "url": "https://music.apple.com/ca/album/gs-up-feat-max-b/78548856?i=78548369&uo=4"
                }
            }
            {
                "type": "song",
                "library": "itunes",
                "name": "G's Up (feat. Max B)",
                "artwork_url": "https://audio-ssl.itunes.apple.com/itunes-assets/Music/v4/ff/65/2f/ff652f2b-c347-ef2f-7e86-3c0c32f11dcd/mzaf_5935542688038353189.plus.aac.p.m4a",
                "info": {
                    "preview_url": "https://audio-ssl.itunes.apple.com/itunes-assets/Music/v4/ff/65/2f/ff652f2b-c347-ef2f-7e86-3c0c32f11dcd/mzaf_5935542688038353189.plus.aac.p.m4a",
                    "title": "G's Up (feat. Max B)",
                    "collection": "Harlem: Diary of a Summer",
                    "artist": "Jim Jones",
                    "languages": [
                        "EN",
                        "ES"
                        ],
                    "rating": 7.5,
                    "genres": [
                        "soul", 
                        "hip/hop"
                        ],
                    "description": "",
                    "more_info":"",
                    "release_date": "2005-08-23",
                    "country": "US",
                    "price": 2.9,
                    "rental_price": 0.99,
                    "currency": "USD",
                    "url": "https://music.apple.com/ca/album/gs-up-feat-max-b/78548856?i=78548369&uo=4"
                }
            },
            ...
        ],
        "limit": 10,
        "next": "https://api.huygens.com/v1/search?query=Muse&type=track&market=US&offset=20&limit=10",
        "offset": 10,
        "previous": "https://api.huygens.com/v1/search?query=Muse&type=track&market=US&offset=0&limit=10",
        "total": 1432
    }
}

```
{% endtab %}
{% endtabs %}
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



