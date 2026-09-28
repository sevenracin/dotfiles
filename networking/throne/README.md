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

1. Tailscale address space from the TUN inbound uses the local `Tailscale` outbound.
2. DNS is hijacked into Throne's configured DNS path.
3. `assettolab.ru`, `steamwebhelper.exe`, international AI services, YouTube, and Apple Intelligence / Private Cloud Compute are forced to `proxy` before broader direct categories can match them.
4. Tailscale processes, Java/Minecraft, and Steam/Epic/Rockstar install paths use `direct`.
5. Broad SagerNet categories for Google, Apple, developer tooling, and games use `direct`. `category-dev` includes GitHub, GitLab, Docker, package managers, programming-language ecosystems, JetBrains, Microsoft developer infrastructure, container tooling and many other development services.
6. Local/private ranges, Russian domains, `geoip-ru`, `geosite-category-ru`, and FunPay use `direct`.
7. Everything unmatched uses the profile's default `proxy` outbound.

AI routing uses SagerNet's maintained `geosite-category-ai-!cn.srs` aggregate instead of separate provider lists. It covers OpenAI, Anthropic, GitHub Copilot, Google DeepMind/Gemini, JetBrains AI, Perplexity, xAI, Cursor, Hugging Face, Groq, OpenRouter, Midjourney, Poe and many other international AI services.

Generic shared CDN/cloud networks such as Cloudflare, Fastly, Akamai and AWS/CloudFront are deliberately not routed `direct` as whole networks because blocked and niche services share them.

## Notes

The profile references an outbound named `Tailscale`. That profile must exist locally in Throne for the Tailscale rule to use it.

DNS server selection is a separate Throne setting and is not stored in this remote routing profile. The profile only contains the DNS hijack routing rule.

Torrents are intentionally not handled by this profile because they already bypass the Throne TUN in the local setup.

Edit `routing.json` in this repository to change the remotely managed routing rules.
