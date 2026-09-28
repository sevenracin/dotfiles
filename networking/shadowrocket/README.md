# Shadowrocket

Public Shadowrocket configuration used from GitHub.

## Config URL

https://raw.githubusercontent.com/sevenracin/dotfiles/main/networking/shadowrocket/shadowrocket.conf

Add this URL to Shadowrocket as a remote configuration. The config contains the same URL in `update-url`, so later edits can be pulled without recreating the configuration.

## Routing policy

The profile is intentionally **PROXY by default**. Unknown and niche services therefore keep working without maintaining a complete censorship list, while broad high-confidence categories bypass the VPN for native speed.

Rule order is important:

1. LAN and Tailscale are `DIRECT`.
2. Advertising is rejected.
3. Narrow foreign-IP exceptions are `PROXY` before broad direct categories can match them. This includes OpenAI, Gemini, YouTube, GitHub/Microsoft Copilot, `assettolab.ru`, Medium, JetBrains AI/Grazie, the maintained custom proxy list, and Apple Intelligence / Private Cloud Compute endpoints.
4. Broad maintained Blackmatrix7 sets for Apple, Google, GitHub, Developer tooling, and Games are `DIRECT`.
5. `.ru`, `.su`, `.рф`, FunPay, and `GEOIP,RU` are `DIRECT`.
6. Everything unmatched is `PROXY`.

The Developer aggregate covers many ecosystems at once, including GitLab, Docker, Python, package/container tooling, JetBrains-related infrastructure, Stack Overflow and other development services. OpenAI and Medium are explicitly caught before this aggregate because they should not use the Russian route.

The Game aggregate covers a large cross-vendor set rather than maintaining individual rules for each publisher/platform.

Generic shared CDN/cloud networks such as Cloudflare, Fastly, Akamai and AWS/CloudFront are deliberately not routed `DIRECT` as whole networks because blocked and niche services share them.

The config intentionally keeps:

- `udp-policy-not-supported-behaviour = DIRECT`
- `block-quic = always-allow`
- IPv6 disabled
- system DNS for DIRECT traffic and DoH through the proxy for proxied traffic

## Private material

Do not commit proxy credentials, subscription URLs, API keys, authentication tokens, private keys, `ca-p12`, or `ca-passphrase` values.

Keep the MITM CA local to Shadowrocket. The public config only enables MITM and does not contain CA private material.
