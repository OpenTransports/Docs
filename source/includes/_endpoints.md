# Endpoints

## Agencies

> Example

```shell
curl "https://server-url.com/agencies?latitude=48.86&longitude=2.35"
```

> Response

```json
[
	{
		"id": "FR/Paris/RATP",
		"name": "RATP",
		"url": "https://ratp.fr",
		"radius": 20000,
		"center": {
			"latitude": 48.856,
			"longitude": 2.35
		},
		"types": [
			{
				"id": 0,
				"name": "Tram",
				"icon": "https://server-url.com/medias/ferre/indices-ferres-2017.05/L_T"
			},
			...
		],
	}
]
```

Returns the list of supported agencies by the server. Each agencies contains informations about the kind of transports it supports.

### HTTP Request

`GET https://<server>/agencies`

### URL Parameters

Parameter          | Default | Description
------------------ |:-------:| -----------
latitude/longitude | 0       | Return the agencies covering the position
radius             | 200     | The search radius from the given position



## Transports

> Example

```shell
curl "https://server-url.com/transports?latitude=48.86&longitude=2.35&radius=200&realtime=true"
```

> Response

```json
[
	{
		"id": "3764645",
		"agencyID": "FR.Paris.RATP",
		"type": 3,
		"name": "LES HALLES - CENTRE GEORGES POMPIDOU",
		"line": "38",
		"position": {
			"latitude": 48.86069953105734,
			"longitude": 2.34956822574239
		},
		"informations": [
			{
				"title": "Montsouris",
				"content": ["2 mn", "3 mn"],
				"timestamp": 123456765
			}
		],
		"iconURL": "https://server-url.com/medias/bus/indices/38genRVB.png"
	},
	...
]
```

Get all transports by the server. This endpoint might need a position to prevent returning to much data. This comportment is the responsibility of the owner.

### HTTP Request

`GET https://<server>/transports`

### URL Parameters

Parameter          | Default | Description
------------------ |:-------:| -----------
latitude/longitude | 0       | Return the transports around the position
radius             | 200     | The search radius from the given position
realtime           | false   | Get the real-time data if possible


## Transport

> Example

```shell
curl "https://server-url.com/transports/3764645?realtime=true"
```

> Response

```json
{
	"ID": "3764645",
	"agencyID": "FR.Paris.RATP",
	"type": 3,
	"name": "LES HALLES - CENTRE GEORGES POMPIDOU",
	"line": "38",
	"position": {
		"latitude": 48.86069953105734,
		"longitude": 2.34956822574239
	},
	"passages": [],
	"iconURL": "https://server-url.com/medias/bus/indices/38genRVB.png"
}
```

Get the information of a transport using its ID

### HTTP Request

`GET https://<server>/transports/<transport-id>`

### URL Parameters

Parameter          | Default | Description
------------------ |:-------:| -----------
realtime           | false   | Get the real-time data if possible
