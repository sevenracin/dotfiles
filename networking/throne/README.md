# Throne

Remote Throne routing profile maintained from GitHub.

## Remote profile URL

https://raw.githubusercontent.com/sevenracin/dotfiles/main/networking/throne/routing.json

The file is a `throne-route-profile` JSON object. Throne can fetch it as a remote routing profile and update the local profile when the remote source changes.

## Install link

Use this once to add the GitHub-hosted route as a remote routing profile:

throne://remoteroute/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3NldmVucmFjaW4vZG90ZmlsZXMvbWFpbi9uZXR3b3JraW5nL3Rocm9uZS9yb3V0aW5nLmpzb24jUm91dGluZw

When Throne asks, keep `Auto update` enabled.

## Routing policy

- Tailscale address space from the TUN inbound uses the local `Tailscale` outbound.
- Tailscale itself, local/private traffic, Russian domains/IPs, Java, and supported game-platform installs use `direct`.
- `assettolab.ru` and `steamwebhelper.exe` explicitly use `proxy` before broader direct rules can match them.
- `geosite-category-ads-all` is rejected.
- All unmatched traffic uses `proxy`.

## Notes

The profile references an outbound named `Tailscale`. That profile must exist locally in Throne for the Tailscale rule to use it.

DNS server selection is a separate Throne setting and is not stored in this remote routing profile. The profile only contains the DNS hijack routing rule.

Edit `routing.json` in this repository to change the remotely managed routing rules.
