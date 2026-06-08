# Assetto Corsa EVO - AMP Template

Custom AMP Generic Module template scaffold for Assetto Corsa EVO dedicated server hosting.

This project was cloned from your ETS2 template and cleaned to keep only ACEVO files.

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
3. Add your repository or copy these files into your AMP datastore templates path.
4. Fetch templates.
5. Create a new Generic Module instance from this template.

## Notes

- This repository is now ACEVO-only (ETS2/ATS files removed).
- Keep config and update values aligned with the current official Assetto Corsa EVO dedicated server release on Steam.
