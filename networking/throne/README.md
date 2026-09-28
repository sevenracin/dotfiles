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

The remote route covers Tailscale peer IPs and full `*.ts.net` destinations.

### MagicDNS

Throne 1.3.0 only auto-generates its Tailscale DNS server when Tailscale is the selected main profile. In this setup the main profile is the Auto Selector and Tailscale is an auxiliary routed endpoint, so short MagicDNS names need a local custom DNS object.

The matching object is stored in [`dns.json`](dns.json).

In **Routing → DNS**:

1. Enable **Use Custom DNS Object**.
2. Open **Edit DNS Object**.
3. Paste the contents of `dns.json`.
4. Save and restart the active profile.

The custom DNS object keeps the existing routing philosophy:

- Tailscale MagicDNS and single-label tailnet names use the embedded Tailscale resolver.
- International AI, YouTube, Apple Intelligence and `assettolab.ru` use Google DoH through `proxy`.
- Broad DIRECT categories and Russian domains use the local resolver.
- Everything else uses Google DoH through `proxy`.

The Tailscale DNS server references endpoint tag `route-0`. Throne generates this tag for the first routed auxiliary outbound. The routing profile intentionally keeps `Tailscale` as the first and only custom routed outbound, so `route-0` is stable in the current design. If another named outbound is later added ahead of Tailscale, update the endpoint tag in `dns.json` to match Throne's generated Tailscale endpoint tag.

With `accept_search_domain` enabled, names such as `gb` can be expanded against the tailnet's MagicDNS search domain without installing the separate Windows Tailscale client.

## Notes

`routing.json` is remotely managed. `dns.json` is a local Throne DNS object and must currently be pasted into Throne manually; it is not imported by the remote route profile.

Torrents are intentionally not handled by this profile because they already bypass the Throne TUN in the local setup.

Edit `routing.json` in this repository to change the remotely managed routing rules.
