# Data types

## Agency
```typescript
id     string // The unique identifier for the agency. Must be CountryCode/City/AgencyName
name   string // The name of the agency (Displayed)
url    string // The url to the agency website
radius int    // The radius covered by the agency
center {      // The central point of the agency
  latitude : float
  longitude: float
}
types [       // The types of transports supported by the agency
	{
		type int    // The type of the transports (See: Transports types)
		name string // A custom display name (Optional: Default to the generic ones)
		icon string // Generic icon (Optional: Default to the generic ones)
	}
]
```

## Transport

```typescript
id       string // Unique id of the transport (Used to retrieve information on the server)
agencyID string // The ID of the agency
type     int    // The type of transport (See: Transports Types)
name     string // The name of the transports (Displayed)
line     string // The line of the transports. (Optional: not necessary for Bikes or Cars)
iconURL  string // The url of an icon to display (Optional: will default to the generic icons from the agency)
position {      // The position of the transport
	latitude  float
	longitude float
}
informations [ // Information on the transports, either next passages or the amount of available bikes (Optional)
	{
		title     string   // The title of the content (Displayed)
		content   string[] // The content of the information (Displayed)
		warn      boolean  // If the content is a warning (Optional, Default: false)
		timestamp boolean  // When the information was retrieve (Optional: if not real-time, Default: 0)
	}
]
```

## Transports Types

```typescript
Tram      0
Metro     1
Rail      2
Bus       3
Ferry     4
Cable     5
Gondola   6
Funicular 7
Bike      8
Car       9
Unknown   10
```

Adapted from [Google specification](https://developers.google.com/transit/gtfs/reference/routes-file). Only difference is the presence of `Bike` and `Car`
