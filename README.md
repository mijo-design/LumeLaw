# LumeLaw
LumeLaw is a global driving light regulation API, designed to be incorporated into car infotainment systems. The goal is to provide cars with an easy-to-understand API for delivering accurate and up-to-date light regulations based on geolocation, vehicle type, and weather conditions. This project aims to enhance driver awareness and compliance with local driving laws, thereby increasing road safety.

 ## API Idea

- country (string): The country code.
- vehicleType (string): The type of vehicle.
- lightsRequired (object): An object with boolean values indicating if lights are required during the day, night, and when it's raining.
- DRL (object): An object indicating if DRLs are required or allowed and additional details.
- roadTypes (array): An array of strings representing types of roads where specific light rules apply.
- timeOfYear (object): An object indicating the time of year when certain light rules apply.
- dimmedHeadlights (object): An object indicating if dimmed headlights are allowed and additional details about when they can be used.
- fogLights (object): An object indicating if fog lights are allowed and additional details about when they can be used.
- updated (string): The date when this information was last updated.

 `GET /countries/{countryCode}/{vehicleType}`
 

```json
{
  "country": "DE",
  "vehicleType": "Car",
  "lightsRequired": {
    "day": {
      "required": false,
      "roadTypes": ["Highway", "Urban", "Rural"],
      "timeOfYear": {"from": "January", "to": "December"}
    },
    "night": {
      "required": true,
      "roadTypes": ["Highway", "Urban", "Rural"],
      "timeOfYear": {"from": "January", "to": "December"}
    },
    "rain": {
      "required": true,
      "roadTypes": ["Highway", "Urban", "Rural"],
      "timeOfYear": {"from": "January", "to": "December"}
    }
  },
  "DRL": {
    "required": false,
    "allowed": true,
    "details": "DRLs are not required but are recommended."
  },
  "dimmedHeadlights": {
    "allowed": true,
    "details": "Dimmed headlights can be used in well-lit urban areas.",
    "roadTypes": ["Urban"],
    "timeOfYear": {"from": "January", "to": "December"}
  },
  "fogLights": {
    "allowed": true,
    "details": "Fog lights can be used when visibility is severely reduced.",
    "roadTypes": ["Rural"],
    "timeOfYear": {"from": "January", "to": "December"}
  },
  "updated": "2023-07-27"
}
```
