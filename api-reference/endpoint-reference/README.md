---
description: The endpoints are arranged in a structure defined by an object model.
---

# Endpoint Reference

## Object Model

A full list of the objects returned by the endpoints of the Huygens Search API. All API endpoints return data in [JSON format](https://www.json.org/json-en.html) and wrapped in a standard Request and Response Object. When a collection of objects is returned and the number of objects is variable, the collection is wrapped in a **Paging Object**  to simplify retrieval of further objects. 

## Request Object

{% tabs %}
{% tab title="Definition" %}
| KEY | TYPE | RULE | VALUE |
| :--- | :--- | :--- | :--- |
| info | Object | Required | Useful device information |
| info.device | String | Required | Type of device from which the request is made |
| info.uuid | String | Required | Universally unique identifier |
| info.os | String | Required | Device OS name |
| info.os\_version | String | Required | Device OS version |
| info.timezone | String | Required | Device OS time zone in [UTC Time Offsets](https://www.utctime.net/utc-time-zone-offsets) format |
| info.language | String | Required | Application language in [ISO 639-1](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) code. |
| content | Object | Optional | Endpoint specific request object  |
{% endtab %}

{% tab title="Example" %}

{% endtab %}
{% endtabs %}

```
$ give me super-powers
```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Once you're strong enough, save the world:

{% code title="hello.sh" %}
```bash
# Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```
{% endcode %}



