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
{% api-method-parameter name="Content-Type" type="string" required=true %}
Value: `application/json`
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" required=true type="string" %}
A valid Bearer Authentication Token from the Huygens API: see the **Authorization Guide** for details.
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
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter type="string" name="--data-raw" required=true %}
**Request** object
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
On success, the response body contains an **Item Search** object wrapped in a **Paging** and **Response** object in JSON.  
  
**Example**:
{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Request" %}
```php
curl --location --request GET 'https://api.huygens.com/v1/search?q=name:Pink%20Floyd&type=artist,song&limit=3' \
--header 'Authorization: Bearer Y2x1YkJJdiQzcjpiaVA0c3N2djByZA==' \
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
    }
}'
```
{% endtab %}

{% tab title="Response" %}
```http
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
                "artwork": "https://audio-ssl.itunes.apple.com/itunes-assets/Music/v4/ff/65/2f/ff652f2b-c347-ef2f-7e86-3c0c32f11dcd/mzaf_5935542688038353189.plus.aac.p.m4a",
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
                "artwork": "https://audio-ssl.itunes.apple.com/itunes-assets/Music/v4/ff/65/2f/ff652f2b-c347-ef2f-7e86-3c0c32f11dcd/mzaf_5935542688038353189.plus.aac.p.m4a",
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

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
The header status code is an error code.  
The response body contains a **Response** object whit error information and error code.  
  
**Example**:
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

### Writing a Query - Guidelines

**Encode spaces** with the hex code `%20` or `+`. 

**Keyword matching**: Matching of search keywords is _not_ case-sensitive. Operators, however, should be specified in uppercase. Unless surrounded by double quotation marks, keywords are matched in any order. For example: `q=roadhouse&20blues` matches both “Blues Roadhouse” and “Roadhouse of the Blues”. `q="roadhouse&20blues"` matches “My Roadhouse Blues” but not “Roadhouse of the Blues”.

**Operator**: The operator **`NOT`** can be used to exclude results. 

For example: `q=roadhouse%20NOT%20blues` returns items that match “roadhouse” but excludes those that also contain the keyword “blues”. 

_Note_: Operators must be specified in uppercase. Otherwise, they are handled as normal keywords to be matched.

**Field filters**: By default, results are returned when a match is found in _any_ field of the target object type. Searches can be made more specific by specifying a `name, artist, album, genre, year and` [`country`](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) field filter. 

For example: The query `q=album:gold%20artist:abba&type=album` returns only albums with the text “gold” in the album name and the text “abba” in the artist name. 

To limit the results to a particular `year`, use the field filter year with album, artist, and track searches. 

For example: `q=bob%20year:2014` 

Or with a date range. For example: `q=bob%20year:1980-2020`

### Item Search Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| type | `String` | **`Required`** | Multimedia resource type |
| library | `String` | **`Required`** | Origin of the multimedia resource |
| name | `String` | **`Required`** | Multimedia resource name |
| artwork | `String` | **`Required`** | Multimedia resource artwork  |
| info | `Object` | **`Required`** | Multimedia resource information |
| info.preview\_url | `String` | `Optional` | Preview multimedia resource |
| info.title | `String` | `Optional` | Song, movie, cast... title |
| info.collection | `String` | `Optional` | Artwork collection |
| info.artist | `String` | `Optional` | Artwork artist |
| info.languages | `Array(String)` | `Optional` | Available languages in [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) code. |
| info.rating\_avg | `Float` | `Optional` | Rating average |
| info.genres | `Array(String)` | `Optional` | Artwork genres |
| info.description | `String` | `Optional` | Description |
| info.more\_info | `String` | `Optional` | Additional artwork information |
| info.release\_date | `String` | `Optional` | Release date to the public |
| info.country | `String` | `Optional` | Country of origin.  See [country codes](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) format. |
| info.price | `Float` | `Optional` | Price of the artwork |
| info.rental\_price | `Float` | `Optional` | Rental price of the artwork |
| info.currency | `String` | `Optional` | Currency |
| info.url | `String` | `Optional` | Artwork URL |
{% endtab %}

{% tab title="JSON Example" %}
```text
{
    "type": "song",
    "library": "itunes",
    "name": "G's Up (feat. Max B)",
    "artwork": "https://audio-ssl.itunes.apple.com/itunes-assets/Music/v4/ff/65/2f/ff652f2b-c347-ef2f-7e86-3c0c32f11dcd/mzaf_5935542688038353189.plus.aac.p.m4a",
    "info": {
        "preview_url": "https://audio-ssl.itunes.apple.com/itunes-assets/Music/v4/ff/65/2f/ff652f2b-c347-ef2f-7e86-3c0c32f11dcd/mzaf_5935542688038353189.plus.aac.p.m4a",
        "title": "G's Up (feat. Max B)",
        "collection": "Harlem: Diary of a Summer",
        "artist": "Jim Jones",
        "languages": [
            "es",
            "en"
            ],
        "rating_avg": 7.5,
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
```
{% endtab %}
{% endtabs %}

