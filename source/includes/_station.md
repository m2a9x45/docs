# Station

## Find Station

```ruby
require "uri"
require "net/http"

url = URI("https://api.yeahtrain.com/station/lookup?name={stationName}")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)
request["X-API-KEY"] = "{API_KEY}"

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.yeahtrain.com/station/lookup?name={stationName}"

payload={}
headers = {
  'X-API-KEY': '{API_KEY}'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request GET 'https://api.yeahtrain.com/station/lookup?name={stationName}' \
--header 'X-API-KEY: {API_KEY}'
```

```javascript
async function getDepatures(token) {
    const response = await fetch('https://api.yeahtrain.com/station/lookup?name={stationName}', {
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
        "crs_code": "EDB",
        "name": "Edinburgh",
        "lat": "55.95238716",
        "long": "-3.188221921",
        "address": [
            "Edinburgh station",
            "Princes Street",
            "Edinburgh",
            "Lothian"
        ],
        "post_code": "EH1 1BB"
    },
    {
        "crs_code": "EGY",
        "name": "Edinburgh Gateway",
        "lat": "55.941000",
        "long": "-3.32000",
        "address": [
            "Edinburgh Gateway station",
            "1 Myreton Drive",
            "Gogar",
            "Lothian"
        ],
        "post_code": "EH12 9GF"
    },
]
```

This endpoint retruns stations for a given serach term. 

### HTTP Request

`GET https://api.yeahtrain.com/station/lookup?name={STATION_NAME}`

### Query Parameters

Parameter | Description
--------- | -----------
STATION_NAME | Search term of a minimum of 3 characters, such as `abe`, `edi` or `london`