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

The route follows the same lean rule used by the Shadowrocket profile: an explicit proxy rule is only kept when a later `direct` rule would otherwise steal that traffic. There is no giant route-level advertising category and no broad AI rule when the default outbound already provides the desired result.

Rule priority:

1. Tailscale peer address space (`100.64.0.0/10` and `fd7a:115c:a1e0::/48`) and `*.ts.net` destinations use the local Throne profile named `Tailscale`.
2. `assettolab.ru` stays on the normal `proxy` outbound despite Russian routing later.
3. Google AI uses a dedicated local outbound named `Google AI` through `geosite-google-deepmind`.
4. GitHub Copilot and JetBrains AI use `proxy` before the developer aggregate can match them. YouTube uses `proxy` before the Google aggregate can match it. Apple Intelligence / Private Cloud Compute is also forced to `proxy` before Apple core routing.
5. `steamwebhelper.exe` uses `proxy`; Java/Minecraft and Steam/Epic/Rockstar install paths use `direct`.
6. Broad built-in Throne rule sets for Google, Apple, developer tooling, and games use `direct`.
7. Local/private ranges, Russian domains, `geoip-ru`, `geosite-category-ru`, and FunPay use `direct`.
8. Everything unmatched uses the profile's default `proxy` outbound.

The profile uses Throne's built-in rule-set names rather than raw `.srs` URLs. This lets Throne resolve and cache the current rule-set URLs itself and avoids duplicate generated remote-rule-set tags.

### Why the broad AI category was removed

The previous route used `geosite-category-ai-!cn`. Most of that set was redundant because the profile already defaults to `proxy`.

Only AI traffic that overlaps a broad `direct` aggregate needs an explicit override:

- `geosite-google-deepmind` — separated into the dedicated `Google AI` outbound because `geosite-google` includes Google AI.
- `geosite-github-copilot` — forced to `proxy` because the developer category includes GitHub.
- `geosite-jetbrains-ai` — forced to `proxy` because the developer category includes JetBrains.

OpenAI, Anthropic/Claude, Microsoft Copilot, Perplexity, xAI/Grok, Cursor, Hugging Face, Groq, OpenRouter, Midjourney, Poe and similar foreign AI services simply fall through to the default `proxy` outbound. No extra rule is needed.

### Google AI dedicated outbound

Create or rename the desired local Throne profile/outbound to exactly:

`Google AI`

Then press **Fetch** on the remote `Routing` profile. Throne resolves named outbounds when the remote route is imported, so the `Google AI` rule should show that local outbound instead of `proxy`.

Use a stable server with a clean exit IP and avoid automatic exit rotation when possible. Gemini and other Google AI products perform aggressive VPN/risk checks, so keeping the same working egress is preferable to a frequently changing auto-selected node.

The `geosite-google-deepmind` set covers Gemini, DeepMind, Generative Language API, AI Studio, NotebookLM, Jules, Google AI Labs/Flow, Gemini Code Assist, Android Studio Gemini, Opal, Antigravity, and Stitch.

## Why there is no route-level ad block

The routing profile intentionally does not load `geosite-category-ads-all`. Ad blocking is better handled by browser/content filters or dedicated blocking layers instead of expanding the core routing table for every connection.

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

Set **Remote Rule-set Mirror** to **GitHub**, stop the active profile, and press **Fetch** in the remote `Routing` profile. If an old duplicate-tag error remains, delete only the local **Routing route profile** and re-add it from the install link above. Do not delete the Infrastructure `Tailscale` profile.

## Notes

Torrents are intentionally not handled by this profile because they already bypass the Throne TUN in the local setup.

Edit `routing.json` in this repository to change the remotely managed routing rules.
