# Service

## Get Service

```ruby
require "uri"
require "net/http"

url = URI("https://api.yeahtrain.com/service/{serviceID}")

http = Net::HTTP.new(url.host, url.port);
request = Net::HTTP::Get.new(url)
request["X-API-KEY"] = "{API_KEY}"

response = http.request(request)
puts response.read_body
```

```python
import requests

url = "https://api.yeahtrain.com/service/{serviceID}"

payload={}
headers = {
  'X-API-KEY': '{API_KEY}'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request GET 'https://api.yeahtrain.com/service/{serviceID}' \
--header 'X-API-KEY: {API_KEY}'
```

```javascript
async function getDepatures(token) {
    const response = await fetch('https://api.yeahtrain.com/service/{serviceID}', {
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

This endpoint retruns service information for a given service ID. 

### HTTP Request

`GET https://api.yeahtrain.com/service/{SERVICE_ID}`

### Query Parameters

Parameter | Description
--------- | -----------
SERVICE_ID | A `service_id` returned either depature endpoing (4993678KNGX____)