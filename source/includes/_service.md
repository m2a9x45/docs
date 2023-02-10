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
  const response = await fetch(
    "https://api.yeahtrain.com/service/{serviceID}",
    {
      headers: {
        "X-API-KEY": token,
        "Content-Type": "application/json",
      },
    }
  );

  const json = await response.json();
  return json;
}
```

```json
[
  {
    "depature_time": "23:33",
    "status": "On time",
    "platform": "3",
    "train_length": null,
    "operator": {
      "name": "London North Eastern Railway",
      "code": "GR"
    },
    "service_type": "train",
    "origin": "London Kings Cross",
    "stops": [
      {
        "station": "Peterborough",
        "time": "00:17",
        "status": "On time"
      },
      {
        "station": "Grantham",
        "time": "00:45",
        "status": "On time"
      },
      {
        "station": "Newark North Gate",
        "time": "00:58",
        "status": "On time"
      },
      {
        "station": "Doncaster",
        "time": "01:25",
        "status": "On time"
      },
      {
        "station": "Leeds",
        "time": "02:20",
        "status": "On time"
      }
    ]
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