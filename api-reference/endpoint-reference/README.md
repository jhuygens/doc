---
description: The endpoints are arranged in a structure defined by an object model.
---

# Endpoint Reference

## Object Model

A full list of the objects returned by the endpoints of the Huygens Search API. All API endpoints return data in [JSON format](https://www.json.org/json-en.html) and wrapped in a standard [Request](./#request-object) and [Response](./#response-object) object. When a collection of objects is returned and the number of objects is variable, the collection is wrapped in a ****[Pag](./#paging-object)i[ng Object](./#paging-object)  to simplify retrieval of further objects. 

## Request Object

This object is a standard required container of the information requested in all API services.

{% tabs %}
{% tab title="Definition" %}
<table>
  <thead>
    <tr>
      <th style="text-align:left">KEY</th>
      <th style="text-align:left">TYPE</th>
      <th style="text-align:left">RULE</th>
      <th style="text-align:left">VALUE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">info</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">Useful device information</td>
    </tr>
    <tr>
      <td style="text-align:left">info.device</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><b><code>Required</code></b>
      </td>
      <td style="text-align:left">
        <p>Type of device from which the request is made.</p>
        <p>Valid values: <code>desktop, phone, tablet</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">info.uuid</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>Optional</code>
      </td>
      <td style="text-align:left">Universally unique identifier</td>
    </tr>
    <tr>
      <td style="text-align:left">info.os</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>Optional</code>
      </td>
      <td style="text-align:left">
        <p>Device OS name.</p>
        <p>Valid values: <code>android, iOS, web</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">info.os_version</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>Optional</code>
      </td>
      <td style="text-align:left">Device OS version in <a href="https://semver.org/">semantic</a> format</td>
    </tr>
    <tr>
      <td style="text-align:left">info.timezone</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>Optional</code>
      </td>
      <td style="text-align:left">Device OS time zone in <a href="https://www.utctime.net/utc-time-zone-offsets">UTC Time Offsets</a> format</td>
    </tr>
    <tr>
      <td style="text-align:left">info.lang</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>Optional</code>
      </td>
      <td style="text-align:left">
        <p>Application language in <a href="https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes">ISO 639-1</a> code.</p>
        <p><b>Note:</b> This API only support English language</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">info.app_name</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>Optional</code>
      </td>
      <td style="text-align:left">Consumer application name</td>
    </tr>
    <tr>
      <td style="text-align:left">info.app_version</td>
      <td style="text-align:left">String</td>
      <td style="text-align:left"><code>Optional</code>
      </td>
      <td style="text-align:left">Consumer application version in <a href="https://semver.org/">semantic</a> format</td>
    </tr>
    <tr>
      <td style="text-align:left">content</td>
      <td style="text-align:left">Object</td>
      <td style="text-align:left"><code>Optional</code>
      </td>
      <td style="text-align:left">Endpoint specific <code>request object </code>
      </td>
    </tr>
  </tbody>
</table>
{% endtab %}

{% tab title="Example" %}
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
        ...
    }
}
```
{% endtab %}
{% endtabs %}

## Response Object

This object is a standard container of the information response in all API services.

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| info | Object | **`Required`** | Useful device information |
| info.type | String | **`Required`** | Response type identifier.  See responses definition table |
| info.title | String | `Optional` | Response message title |
| info.message | String | `Optional` | Response message description |
| info.code | String | `Optional` | Response code |
| content | Object | `Optional` | Endpoint specific `response object`  |
{% endtab %}

{% tab title="Example" %}
```text
{
    "info": {
        "type": "success",
        "title": "Succefull response",
        "message": "",
        "code": "0"
    },
    "content": {
        ...
    }
}
```
{% endtab %}
{% endtabs %}

## Paging Object

The offset-based paging object is a container for a set of objects. It contains a key called `items` \(whose value is an array of the requested objects\) along with other keys like `previous`, `next` and `limit` that can be useful in future calls.

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| href | String | **`Required`** | A link to the API endpoint returning the full result of the request. |
| items | Array\(Object\) | **`Required`** | The requested data. |
| limit | Integer | **`Required`** | The maximum number of items in the response \(as set in the query or by default\). |
| next | String | **`Required`** | URL to the next page of items. \( `null` if none\) |
| offset | Integer | **`Required`** | The offset of the items returned \(as set in the query or by default\). |
| previous | String | **`Required`** | URL to the previous page of items. \( `null` if none\) |
| total | Integer | **`Required`** | The maximum number of items available to return. |
{% endtab %}

{% tab title="Second Tab" %}

{% endtab %}
{% endtabs %}

