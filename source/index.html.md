---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - depWithDetails
  - service
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
```

> Make sure to replace `meowmeowmeow` with your API key.

We use API keys to allow access to the API. You can register a new API key within the [developer portal](http://example.com/developers).

Your expected to include your API key in all API requests to the server in a custom header that looks like the following:

`x-api-key: {API_KEY}`

<aside class="notice">
You must replace <code>{API_KEY}</code> with your personal API key. Your API will start with `key_`
</aside>

# Depatures

## Get All Depatures

```ruby
require "uri"
require "net/http"

url = URI("localhost:3000/station/kgx/departures")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)
request["X-API-KEY"] = "{API_KEY}"

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.localhost.com/station/kgx/departures"

payload={}
headers = {
  'X-API-KEY': '{API_KEY}'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request GET 'localhost:3000/station/kgx/departures' \
--header 'X-API-KEY: {API_KEY}'
```

```javascript
async function getDepatures(token) {
    const response = await fetch('https://api.localhost.com/station/kgx/departures', {
        headers: {
            'X-API-KEY': token,
            'Content-Type': 'application/json'
        }
    })

    const json = await response.json();
    return json
}
```

> The above command returns JSON structured like this:

```json
[
  {
    "depature_time": "21:42",
    "status": "On time",
    "platform": "9",
    "operator": {
        "name": "Great Northern",
        "code": "GN"
    },
    "service_type": "train",
    "service_id": "4993678KNGX____",
    "origin": "London Kings Cross",
    "destination": "Kings Lynn"
  },
  {
    "depature_time": "21:58",
    "status": "On time",
    "platform": "TBC",
    "operator": {
        "name": "Thameslink",
        "code": "TL"
    },
    "service_type": "train",
    "service_id": "4995645KNGX____",
    "origin": "London Kings Cross",
    "destination": "Cambridge"
  }
]
```

This endpoint retruns up to 150 live depatures from the specifed station

### HTTP Request

`GET http://example.com/api/station/{CRS_CODE}/departures`

### Query Parameters

Parameter | Description
--------- | -----------
CRS_CODE | A 3 letter station code (KGX, ABR)

<aside class="notice">
A list of CRS codes can be found <a href="https://www.nationalrail.co.uk/stations_destinations/48541.aspx">here</a>
</aside>