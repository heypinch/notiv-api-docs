---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='mailto:developers@notiv.com?subject=Can I please get API Access?'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Notiv API! You can use our API to access Notiv API endpoints, which can create new meetings or retrieve information on your existing meetings in our database.

We have provided example calls in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

We strive to keep our documentation as up to date as possible. If you feel you have found an issue in this documentation, please submit an issue or pull request at [https://github.com/heypinch/notiv-api-docs](https://github.com/heypinch/notiv-api-docs)

# Authentication

> To authorize, use this code:

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.notiv.com/v1/meetings")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["Authorization"] = 'bearer keykeykeykeykey' # substitute your key here

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.notiv.com/v1/meetings"

headers = {
    'Authorization': "bearer keykeykeykeykey"
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: bearer keykeykeykeykey"
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.notiv.com/v1/meetings");
xhr.setRequestHeader("Authorization", "bearer keykeykeykeykey");

xhr.send(data);
```

> Make sure to replace `keykeykeykeykey` with your API key.

Notiv uses API keys to allow access to the API. If you would like to have API access enabled on your account, please email us at [developers@notiv.com](mailto:developers@notiv.com).

Notiv expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: bearer keykeykeykeykey`

<aside class="notice">
You must replace <code>keykeykeykeykey</code> with your personal API key.
</aside>

# Meetings

## Get All Meetings

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.notiv.com/v1/meetings")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["Authorization"] = 'bearer keykeykeykeykey'

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.notiv.com/v1/meetings"

headers = {
    'Authorization': "bearer keykeykeykeykey",
    }

response = requests.request("GET", url, headers=headers)

print(response.text)
```

```shell
curl "https://api.notiv.com/v1/meetings"
  -H "Authorization: bearer keykeykeykeyley"
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.notiv.com/v1/meetings");
xhr.setRequestHeader("Authorization", "bearer keykeykeykeykey");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
  "meetings": [
    {
      "id": 1,
      "name": "Fluffums",
      "breed": "calico",
      "fluffiness": 6,
      "cuteness": 7
    },
    {
      "id": 2,
      "name": "Max",
      "breed": "unknown",
      "fluffiness": 5,
      "cuteness": 10
    }
  ]
}
```

This endpoint retrieves all meetings.

### HTTP Request

`GET https://api.notiv.com/v1/meetings`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
page | `1` | The requested numeric page number within the matched meeting results
include | empty | A comma seperated list of extra attributes to include in the response, e.g. `owner,transcript`.

<aside class="success">
Remember — always send your API key in the `Authorization` header!
</aside>

## Get a Specific Meeting

```ruby
require 'uri'
require 'net/http'

url = URI("https://api.notiv.com/v1/meetings/<ID>?include=transcript")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)
request["Authorization"] = 'bearer keykeykeykeykey' # substitute your key here

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.notiv.com/v1/meetings/<ID>"

querystring = {"include":"transcript"}

headers = {
    'Authorization': "bearer keykeykeykeykey",
    }

response = requests.request("GET", url, headers=headers, params=querystring)

print(response.text)
```

```shell
curl "https://api.notiv.com/v1/meetings/<ID>"
  -H "Authorization: bearer keykeykeykeykey"
```

```javascript
var data = null;

var xhr = new XMLHttpRequest();
xhr.withCredentials = true;

xhr.addEventListener("readystatechange", function () {
  if (this.readyState === 4) {
    console.log(this.responseText);
  }
});

xhr.open("GET", "https://api.notiv.com/v1/meetings/<ID>?include=transcript");
xhr.setRequestHeader("Authorization", "bearer keykeykeykey");

xhr.send(data);
```

> The above command returns JSON structured like this:

```json
{
  "meeting": {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
}
```

This endpoint retrieves a specific meeting.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://api.notiv.com/v1/meetings/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the meeting to retrieve

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include | empty | A comma seperated list of extra attributes to include in the response, e.g. `owner,transcript`.
