---
title: Earth Genome

language_tabs:
  - shell
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

search: true
---

# Introduction

[The Earth Genome](http://earthgenome.org)'s goal is to answer questions about the planet that are relevant to decision making.  This set of web services provides the basic components of environmental applications.  Think of Twilio for the environment.  These services provide sufficiently high-level information, so that it is useful to decision-making.  Not just barometric readings, but historical weather for irrigation districts.  Not just vegetation indices, but crop types for agricultural aggregations.  

# Authentication

> To authorize, use this code:


```python
import earthgenome

api = earthgenome.authorize('demo_key')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: demo_key"
```

> Make sure to replace `demo_key` with your API key.

The Earth Genome service uses API keys to allow access to the API. You can register a new API key at our [developer portal](http://example.com/developers).

The Earth Genome expects the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: demo_key`

<aside class="notice">
You must replace <code>demo_key</code> with your personal API key.
</aside>

# Residential valuation

## Coastal properties and sea level rise

This web service reports the implied value of coastal real estate from the combined estimates of NOAA, Zillow, and over 90 peer-reviewed studies of climate change.  It is the best available, comprehensive assessment of coastal real estate under conditions of climate change, served as a proper web service.  

```python
import requests

payload = {'api_key': 'DEMO_KEY'}
base = 'http://api.earthgenome.org/'
address = '275+Beresford+Creek+Street/Daniel+Island/SC/29492'

requests.get(base + address, params=payload)

```

```shell
curl "http://api.earthgenome.org/275+Beresford+Creek+Street/Daniel+Island/SC/29492"
```

> The above command returns JSON structured like this:

```json
{
  "adjusted_valuation": "$772,366.26", 
  "house": {
    "lat": 32.862305, 
    "valuation": "$788,037.00", 
    "lon": -79.919835
  }
}

```

### HTTP Request

`GET http://api.earthgenome.org/<address>/<city>/<state>/<zipcode>`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
api_key | DEMO_KEY | API key associated with your account

<aside class="warning">
The supplied address must be a URL safe address with "+" separation.
</aside>

# Historical weather

This web service provides information on "this day in history" weather for a supplied location.

```python
import requests

payload = {'api_key': 'DEMO_KEY'}
base = 'http://api.earthgenome.org/v1/weather/historical/37.8/-122.4/2011-01-02/2011-01-04'

requests.get(base, params=payload)
```

```shell
curl "http://api.earthgenome.org/v1/weather/historical/37.8/-122.4/2011-01-02/2011-01-04"
```

> The above command returns JSON structured like this:

```json

{
  "latitude": 37.8267,
  "version": 1,
  "results": [
    {
      "date": "2011-01-02",
      "windSpeed": 7.64,
      "precipitation": 0.0252
    },
    {
      "date": "2011-01-03",
      "windSpeed": 10.22,
      "precipitation": 0.0306
    },
    {
      "date": "2011-01-04",
      "windSpeed": 7.52,
      "precipitation": 0
    }
  ],
  "longitude": -122.4233
}
```

### HTTP Request

`GET http://api.earthgenome.org/v1/weather/historica/<lat>/<lon>/<begin-date>/<end-date>`

### URL Parameters

Parameter | Default | Description
--------- | ------- | -----------
api_key | DEMO_KEY | API key associated with your account

