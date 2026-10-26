# Home Hub Card

A wall-tablet card for Home Assistant: an illustrated sleep screen that follows the time of day, the weather and the season, and a dashboard for energy, climate, lights and the garage.

Scenes: Dingli cliffs (default), Halloween (classic and moonlit), Christmas and Carnival. Every scene comes in morning, midday, sunset and night versions, each in sunny, cloudy, rain and windy weather.

```yaml
type: custom:home-hub-card
person: person.me
battery: sensor.battery_soc
climate:
  - entity: climate.living_room
    name: Living Room
lights:
  - entity: light.living_room
    name: Living Room
garage: cover.garage
```
