# LumeLaw
LumeLaw is a global driving light regulation API, designed to be incorporated into car infotainment systems. The goal is to provide cars with an easy-to-understand API for delivering accurate and up-to-date light regulations based on geolocation, vehicle type, and weather conditions. This project aims to enhance driver awareness and compliance with local driving laws, thereby increasing road safety.

 ## API Idea

- country (string): The country code.
- vehicleType (string): The type of vehicle.
- updated (string): The date when this information was last updated.
- lights (object): An object containing specific types of lights.
    - headlights (object): An object describing the regulations for standard headlights.
    - DRL (object): An object describing the regulations for daytime running lights.
    - dimmedHeadlights (object): An object describing the regulations for dimmed headlights.
    - fogLights (object): An object describing the regulations for fog lights.
        - allowed (boolean): Whether these lights are allowed.
        - required (object): When these lights are required.
        - day (boolean): Required during the day.
        - night (boolean): Required during the night.
        - weather (array): Weather conditions when these lights are required.
        - details (string): Additional details about these lights.
        - roadTypes (array): Types of roads where these lights are required or allowed.
        - timeOfYear (object): The time of year when these lights are required or allowed.
     


`GET /countries/{countryCode}/{vehicleType}`
 
```json
{
  "country": "IT",
  "vehicleType": "Car",
  "lights": {
    "headlights": {
      "allowed": true,
      "required": {
        "day": false,
        "night": true,
        "weather": ["Rain", "Snow"]
      },
      "details": "Standard headlights.",
      "roadTypes": ["Highway", "Urban", "Rural"],
      "timeOfYear": {"from": "January", "to": "December"}
    },
    "DRL": {
      "allowed": true,
      "required": {
        "day": true,
        "night": false,
        "weather": ["Clear"]
      },
      "details": "DRLs must be on whenever the vehicle is in operation during the day.",
      "roadTypes": ["Highway", "Urban", "Rural"],
      "timeOfYear": {"from": "January", "to": "December"}
    },
    "dimmedHeadlights": {
      "allowed": true,
      "required": {
        "day": false,
        "night": false,
        "weather": ["Clear"]
      },
      "details": "Dimmed headlights can be used in well-lit urban areas.",
      "roadTypes": ["Urban"],
      "timeOfYear": {"from": "January", "to": "December"}
    },
    "fogLights": {
      "allowed": true,
      "required": {
        "day": false,
        "night": false,
        "weather": ["Fog"]
      },
      "details": "Fog lights can be used when visibility is severely reduced.",
      "roadTypes": ["Rural"],
      "timeOfYear": {"from": "January", "to": "December"}
    }
  },
  "updated": "2023-07-27"
}
```
