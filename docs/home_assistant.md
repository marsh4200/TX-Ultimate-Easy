# Home Assistant Entity Selection

TX Ultimate Easy already fires `esphome.tx_ultimate_easy` button events for:

- `click`
- `double_click`
- `long_press`
- `multiple_click`

If you want a real Home Assistant entity picker that reflects the entities currently
available in your Home Assistant instance, the recommended approach is to keep the
button detection in ESPHome and move the target/action selection into Home Assistant.

## Why

ESPHome template selects use fixed YAML options. Home Assistant automations, scripts,
and blueprints use Home Assistant's own service and entity selectors, which are the
live dropdowns you see in the UI.

## Included Blueprint

This repository now includes a Home Assistant automation blueprint:

`docs/home_assistant/blueprints/automation/tx_ultimate_easy_button_event_action.yaml`

Use it to create one automation per button action you want to handle.

## Example Setup

1. Copy the blueprint file into your Home Assistant config folder:

   `config/blueprints/automation/tx_ultimate_easy/tx_ultimate_easy_button_event_action.yaml`

2. In Home Assistant, go to:

   `Settings -> Automations & Scenes -> Blueprints`

3. Import or reload the blueprint.

4. Create an automation from the blueprint.

5. Pick:

- The TX device name from the event payload, for example `living_room_panel`
- The button number, for example `Button 2`
- The action type, for example `Double-click`
- The Home Assistant action to run

## Example Uses

- Button 1 double-click -> `media_player.media_play_pause` on your TV
- Button 2 double-click -> `light.toggle` on a lamp
- Button 3 long-press -> `scene.turn_on` for a movie scene
- Button 4 click -> `script.turn_on` for a custom script

## Event Reference

You can inspect live events in Home Assistant under:

`Developer Tools -> Events`

Listen to:

`esphome.tx_ultimate_easy`
