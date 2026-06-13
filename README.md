# Assetto Corsa EVO - AMP Template

Custom AMP Generic Module template for Assetto Corsa EVO dedicated server hosting using the headless server binary.

## Files

- assetto-corsa-evo.kvp
- assetto-corsa-evoconfig.json
- assetto-corsa-evometaconfig.json
- assetto-corsa-evo-server_config.json
- assetto-corsa-evoports.json
- assetto-corsa-evoupdates.json
- manifest.json

## Before Using In AMP

Prerequisite: You must own Assetto Corsa EVO on the Steam account used by AMP, and AMP/SteamCMD must be able to log in to Steam for installs and updates.

This template launches `AssettoCorsaEVOServer.exe` directly with:

- `-configjson "{{$FullBaseDir}}server_config.json"`
- `-seasonjson "{{$FullBaseDir}}{{SeasonJsonFile}}"`

The managed server config is generated from `assetto-corsa-evo-server_config.json`.

## Add Template To AMP

1. Open AMP ADS panel.
2. Go to Configuration, then Instance Deployment.
3. In template/app repository sources, add this source:
	- simoneves1/ac-evo-amp:main
4. Save/apply changes.
5. Fetch or refresh templates.
6. Create a new Generic Module instance from this template.

## Recommended First Start

1. Run Update for the new instance.
2. In Application Deployment, verify executable is `AssettoCorsaEVOServer.exe`.
3. In Configuration, keep `Season JSON File` as `events_practice.json` for first boot.
4. Start the instance and watch console for `Listening to TCP`.

## Advanced Field List

The template now includes an `Advanced` section in AMP configuration.

- `Netcode Update Interval`: maps to `netcode_update_interval`
- `PI Minimum` and `PI Maximum`: map to `pi_min` and `pi_max`
- `Tuning Type`: maps to `tuning_type`
- `Allowed Cars JSON`: raw JSON array for `allowed_cars_list_full`
- `Property 1 JSON`, `Property 2 JSON`, `Property 3 JSON`: raw JSON arrays for server properties
- `Entry List Server URL` and `Entry List Path`: map to entry list fields
- `Results POST URL` and `Results Path`: control result upload endpoint and local output path

For all `* JSON` fields, keep the value valid JSON (for example `[]` or `[{"car_name":"preset_695b_mech_1","ballast":0,"restrictor":0}]`).

### AMP Source Format

Use this format when adding a GitHub source in AMP:

- owner/repository:branch

Example used by this template:

- simoneves1/ac-evo-amp:main

## Notes

- This repository is now ACEVO-only (ETS2/ATS files removed).
- The dedicated server app id is `4564210`.
- The server binary supports gflags CLI options including `-configjson` and `-seasonjson`, which this template uses.
- Default exposed ports in this template are TCP `9700`, UDP `9700`, and TCP `8080`.

## Troubleshooting

If AMP logs `exit code -1 (CATASTROPHIC_FAILURE)` right after start:

1. In the instance, run an update first and confirm SteamCMD download succeeds.
2. Confirm the executable path resolves to `AssettoCorsaEVOServer.exe` in `App.BaseDirectory`.
3. Re-check app IDs and Steam login mode:
	- Dedicated server app id: `4564210`
	- `App.SteamUpdateAnonymousLogin=False`
4. Confirm `Season JSON File` points to an existing file (for example `events_practice.json`) in the server base directory.
5. If the instance was created before these template fixes, create a new instance from refreshed templates.
