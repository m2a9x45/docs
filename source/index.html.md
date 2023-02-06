---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://yeahtrain.com'>Sign Up for a API Key</a>

includes:
  - depWithDetails
  # - service

code_clipboard: true

meta:
  - name: description
    content: Documentation for the yeahtrain API
---

# Introduction

👋 Welcome to the yeahtrain API! You can use our API to access UK railway depature information. At the moment this 
is a very simple barebones API but we're looking to add more features soon.

# Authentication

We use API keys to allow access to the API. You can register a new API key within the [developer portal](https://yeahtrain.com/app).

We expect each reqeust to include your API key in a custom header called `x-api-key` that looks like the following:

`x-api-key: {API_KEY}`

<aside class="notice">
You must replace <code>{API_KEY}</code> with your personal API key. Your API will start with `key_`
</aside>

# Depatures

## Get All Depatures

```ruby
require "uri"
require "net/http"

url = URI("https://api.yeahtrain.com/station/kgx/departures")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)
request["X-API-KEY"] = "{API_KEY}"

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.yeahtrain.com/station/kgx/departures"

payload={}
headers = {
  'X-API-KEY': '{API_KEY}'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request GET 'https://api.yeahtrain.com/station/kgx/departures' \
--header 'X-API-KEY: {API_KEY}'
```

```javascript
async function getDepatures(token) {
    const response = await fetch('https://api.yeahtrain.com/station/kgx/departures', {
        headers: {
            'X-API-KEY': token,
            'Content-Type': 'application/json'
        }
    })

    const json = await response.json();
    return json
}
```

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

`GET https://api.yeahtrain.com/station/{CRS_CODE}/departures?numRows=20`

### Query Parameters

Parameter | Required | Default | Description
--------- | ----------- | ----------- | -----------
CRS_CODE | Required | | 3 letter station code (KGX, ABR)
numRows | Optional | 20 | `0` to `150` - Maxium number of rows to be retuned
filterCrs | Optional | | CRS code of either an origin or destination location you'd like to filter to
filterType | Optional |to | `from` or `to` - The type of filter to apply. Filters services to include only those originating or terminating at the filterCrs location
timeOffset | Optional | 0 | `-120` to `120` - An offset in minutes against the current time to provide the station board for
timeWindow | Optional | 120 | `-120` to `120` - How far into the future in minutes, relative to timeOffset, to return services for.

<aside class="notice">
A list of CRS codes can be found <a href="https://www.nationalrail.co.uk/stations_destinations/48541.aspx">here</a>
</aside>