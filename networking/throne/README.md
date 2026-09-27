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

The profile is intentionally **proxy by default**. Unknown and niche services stay on the VPN, while high-confidence traffic bypasses it for maximum native speed.

Rule priority:

1. Tailscale address space from the TUN inbound uses the local `Tailscale` outbound.
2. DNS is hijacked into Throne's configured DNS path.
3. `assettolab.ru`, `steamwebhelper.exe`, AI services, YouTube, and Apple Intelligence / Private Cloud Compute are forced to `proxy` before broader direct rules can match them.
4. Tailscale processes, Java/Minecraft, and Steam/Epic/Rockstar install paths use `direct`.
5. Google core, GitHub core, and Apple core use maintained SagerNet sing-geosite SRS sets and route `direct`.
6. Local/private ranges, Russian domains, `geoip-ru`, `geosite-category-ru`, and FunPay use `direct`.
7. Everything unmatched uses the profile's default `proxy` outbound.

The explicit AI proxy set uses maintained SagerNet rule sets for OpenAI, Anthropic, Perplexity, xAI, Google DeepMind/Gemini, and GitHub Copilot. Microsoft/Windows is not broadly bypassed, so Microsoft Copilot and other Microsoft services remain on the default proxy unless a more specific rule applies.

Generic shared CDN networks such as Cloudflare, Fastly, Akamai, AWS/CloudFront, and similar infrastructure are deliberately not routed DIRECT as a whole.

## Notes

The profile references an outbound named `Tailscale`. That profile must exist locally in Throne for the Tailscale rule to use it.

DNS server selection is a separate Throne setting and is not stored in this remote routing profile. The profile only contains the DNS hijack routing rule.

Torrents are intentionally not handled by this profile because they already bypass the Throne TUN in the local setup.

Edit `routing.json` in this repository to change the remotely managed routing rules.
