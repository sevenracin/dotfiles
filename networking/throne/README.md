# Throne

Remote Throne routing profile maintained from GitHub.

## Remote profile URL

https://raw.githubusercontent.com/sevenracin/dotfiles/main/networking/throne/routing.json

The file is a `throne-route-profile` JSON object. Throne can fetch it as a remote routing profile and update the local profile when the remote source changes.

## Install link

Use this once to add the GitHub-hosted route as a remote routing profile:

throne://remoteroute/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3NldmVucmFjaW4vZG90ZmlsZXMvbWFpbi9uZXR3b3JraW5nL3Rocm9uZS9yb3V0aW5nLmpzb24jUm91dGluZw

When Throne asks, keep `Auto update` enabled.

## Notes

The profile references an outbound named `Tailscale`. That profile must exist locally in Throne for the Tailscale rule to use it.

Edit `routing.json` in this repository to change the remotely managed routing rules.
