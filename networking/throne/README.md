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

The profile is intentionally **proxy by default**. Unknown and niche services stay on the VPN, while broad high-confidence categories bypass it for maximum native speed.

Rule priority:

1. Tailscale peer address space (`100.64.0.0/10` and `fd7a:115c:a1e0::/48`) and full `*.ts.net` destinations use the local Throne profile named `Tailscale`.
2. Throne injects its DNS hijack rule automatically for structured routing profiles; the remote route does not duplicate it.
3. `assettolab.ru`, `steamwebhelper.exe`, international AI services, YouTube, and Apple Intelligence / Private Cloud Compute are forced to `proxy` before broader direct categories can match them.
4. Java/Minecraft and Steam/Epic/Rockstar install paths use `direct`.
5. Broad built-in Throne rule sets for Google, Apple, developer tooling, and games use `direct`.
6. Local/private ranges, Russian domains, `geoip-ru`, `geosite-category-ru`, and FunPay use `direct`.
7. Everything unmatched uses the profile's default `proxy` outbound.

The profile uses Throne's built-in rule-set names rather than raw `.srs` URLs. This lets Throne resolve and cache the current rule-set URLs itself and avoids duplicate generated remote-rule-set tags.

AI routing uses the built-in `geosite-category-ai-!cn` aggregate. It covers OpenAI, Anthropic, GitHub Copilot, Google DeepMind/Gemini, JetBrains AI, Perplexity, xAI, Cursor, Hugging Face, Groq, OpenRouter, Midjourney, Poe and many other international AI services.

Generic shared CDN/cloud networks such as Cloudflare, Fastly, Akamai and AWS/CloudFront are deliberately not routed `direct` as whole networks because blocked and niche services share them.

## Tailscale

A local Throne Tailscale profile named exactly `Tailscale` must exist. The routing profile uses that Throne endpoint directly; a separate Windows Tailscale installation is not required for peer-IP routing.

The remote route covers Tailscale peer IPs and full `*.ts.net` destinations. In Throne 1.3.0, however, a Tailscale profile used only as an auxiliary routing outbound does **not** cause Throne to create its `dns-tailscale` DNS server. Throne currently creates that DNS server only when the selected main profile itself is Tailscale.

Therefore short MagicDNS names such as `gb` cannot be provided by this remote routing JSON alone when the main profile is an Auto Selector. Short-name MagicDNS requires additional local Throne DNS configuration that connects DNS resolution to the Tailscale endpoint. This is separate from traffic routing.

## Notes

DNS server selection is a separate Throne setting and is not stored in this remote routing profile.

Torrents are intentionally not handled by this profile because they already bypass the Throne TUN in the local setup.

Edit `routing.json` in this repository to change the remotely managed routing rules.
