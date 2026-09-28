# Throne

Remote Throne routing profile maintained from GitHub.

## Remote profile URL

https://raw.githubusercontent.com/sevenracin/dotfiles/main/networking/throne/routing.json

The file is a `throne-route-profile` JSON object. Throne can fetch it as a remote routing profile and update the local profile when the remote source changes.

## Install link

Use this once to add the GitHub-hosted route as a remote routing profile:

throne://remoteroute/aHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL3NldmVucmFjaW4vZG90ZmlsZXMvbWFpbi9uZXR3b3JraW5nL3Rocm9uZS9yb3V0aW5nLmpzb24jUm91dGluZw

When Throne asks, keep `Auto update` enabled. In **Routing → Common**, use **GitHub** for **Remote Rule-set Mirror** so remote route updates do not get an older cached copy from a CDN mirror.

## Routing policy

The profile is intentionally **proxy by default**. Unknown and niche services stay on the VPN, while broad high-confidence categories bypass it for maximum native speed.

Rule priority:

1. Tailscale peer address space (`100.64.0.0/10` and `fd7a:115c:a1e0::/48`) and `*.ts.net` destinations use the local Throne profile named `Tailscale`.
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

Peer traffic to Tailscale addresses is routed through that profile. Use a peer's `100.x.x.x` address to verify the Tailscale path independently of DNS.

### MagicDNS limitation in Throne 1.3.0

Do **not** use a custom Tailscale DNS server that references `route-0` in this setup. Throne can build the routed Tailscale profile for traffic, but sing-box fails during DNS initialization when a custom Tailscale DNS server tries to bind to that routed endpoint (`endpoint not found: route-0`).

Throne only wires its generated Tailscale DNS server automatically when Tailscale itself is the selected main profile. With the normal Auto Selector as the main profile and Tailscale used only as a routed outbound, short MagicDNS names such as `gb` are therefore not currently available through Throne alone.

For the stable configuration:

- leave **Use Custom DNS Object** disabled and let Throne generate DNS from the normal DNS settings; or
- if a custom object is required for another reason, [`dns.json`](dns.json) is a startup-safe object without the unsupported Tailscale endpoint binding.

This means `ssh 100.x.x.x` can work through the routed Tailscale profile, while `ssh gb` requires either future Throne support for auxiliary Tailscale DNS, making Tailscale the main selected profile, or a separate Tailscale client that provides MagicDNS to Windows.

## Resetting an old local route

Older revisions of this profile used raw SagerNet `.srs` URLs. Throne turns those URLs into hashed tags such as `geosite-category-ai-!cn-srs-...`. If Throne reports a duplicate tag with that old hashed form, the local `Routing` profile is stale; the current `routing.json` does not contain raw `.srs` URLs.

Set **Remote Rule-set Mirror** to **GitHub**, stop the active profile, and press **Fetch** in the remote `Routing` profile. The AI rule should display `geosite-category-ai-!cn`, not a `raw.githubusercontent.com/...srs` URL. If the duplicate-tag error remains, delete only the local **Routing route profile** and re-add it from the install link above. Do not delete the Infrastructure `Tailscale` profile.

## Notes

Torrents are intentionally not handled by this profile because they already bypass the Throne TUN in the local setup.

Edit `routing.json` in this repository to change the remotely managed routing rules.
