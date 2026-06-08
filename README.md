# Assetto Corsa EVO - AMP Template

Custom AMP Generic Module template scaffold for Assetto Corsa EVO dedicated server hosting.

## Files

- assetto-corsa-evo.kvp
- assetto-corsa-evoconfig.json
- assetto-corsa-evometaconfig.json
- assetto-corsa-evoports.json
- assetto-corsa-evoupdates.json
- assetto-corsa-evo.sii
- manifest.json

## Before Using In AMP

You must replace placeholder values inherited from generic scaffolding:

1. In assetto-corsa-evo.kvp:
- Meta.URL
- Meta.DisplayImageSource
- App.BaseDirectory
- App.ExecutableWin
- App.ExecutableLinux
- App.EnvironmentVariables SteamAppId

2. In assetto-corsa-evoupdates.json:
- UpdateSourceData (dedicated server Steam App ID)
- UpdateSourceArgs (client/game App ID if required by your flow)
- Settings template URL if you host a remote config template

## Add Template To AMP

1. Open AMP ADS panel.
2. Go to Configuration, then Instance Deployment.
3. In template/app repository sources, add this source:
	- simoneves1/ac-evo-amp:main
4. Save/apply changes.
5. Fetch or refresh templates.
6. Create a new Generic Module instance from this template.

### AMP Source Format

Use this format when adding a GitHub source in AMP:

- owner/repository:branch

Example used by this template:

- simoneves1/ac-evo-amp:main

## Notes

- This repository is now ACEVO-only (ETS2/ATS files removed).
- Keep config and update values aligned with the current official Assetto Corsa EVO dedicated server release on Steam.

## Troubleshooting

If AMP logs `exit code -1 (CATASTROPHIC_FAILURE)` right after start:

1. In the instance, run an update first and confirm SteamCMD download succeeds.
2. Confirm the executable path resolves to a real file in `App.BaseDirectory`.
3. Re-check app IDs and Steam login mode:
	- Dedicated server app id: `4564210`
	- `App.SteamUpdateAnonymousLogin=False`
4. If the instance was created before these template fixes, create a new instance from refreshed templates.
