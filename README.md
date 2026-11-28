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

## Alerts

One red tile appears at the top of the dashboard while any alert is active and disappears when all are resolved. Tap it to see the list.

```yaml
alerts:
  - entity: binary_sensor.water_leak      # active while "on" (default)
    name: Water leak
    text: Under the sink
  - entity: sensor.filter_life            # numeric: below / above
    name: Purifier filter
    below: 6
  - entity: sensor.dishwasher_state       # one state or a list
    name: Dishwasher
    state: finished
  - entity: event.backup                  # match an attribute instead of the state
    attribute: event_type
    state: failed
    name: Backup failed
  - entity: camera.garage                 # active while unavailable
    name: Garage camera
    unavailable: true
```

## Pausing a light's automation

Give a light a `pause` helper (an `input_boolean`) when an automation switches it on by itself. The tile shows "Off · paused" while it is on, and the light's sheet gets an Automatic / Paused choice. The card only flips the helper; your automation decides what a pause means.

```yaml
lights:
  - entity: light.terrace
    name: Terrace lights
    timer: timer.terrace_off_timer
    pause: input_boolean.terrace_lights_auto_paused
```
