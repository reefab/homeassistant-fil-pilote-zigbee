# homeassistant-fil-pilote-zigbee
How to control a "fil pilote" heater from Home Assistant using Zigbee

```yaml
switch:
  - platform: template
    switches:
      towel_dryer:
        value_template: "{{ is_state('switch.sonoff_mini_1', 'off') }}"
        turn_on:
          service: switch.turn_off
          entity_id: switch.sonoff_mini_1
        turn_off:
          service: switch.turn_on
          entity_id: switch.sonoff_mini_1

climate:
  - platform: generic_thermostat
    name: Bathroom
    heater: switch.towel_dryer
    target_sensor: sensor.multi_2_temperature
    comfort_temp: 20
    away_temp: 0
```
