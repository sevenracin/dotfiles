# Shadowrocket

Public Shadowrocket configuration used from GitHub.

## Config URL

https://raw.githubusercontent.com/sevenracin/dotfiles/main/networking/shadowrocket/shadowrocket.conf

Add this URL to Shadowrocket as a remote configuration. The config contains the same URL in `update-url`, so later edits can be pulled without recreating the configuration.

## Routing policy

The profile is intentionally **PROXY by default**. Unknown and niche services therefore work without maintaining a complete censorship list, while high-confidence traffic is routed directly for speed.

Rule order is important:

1. LAN and Tailscale are `DIRECT`.
2. Advertising is rejected.
3. Narrow exceptions that need a foreign IP are `PROXY` before any broad direct family can match them. This includes Gemini, YouTube, GitHub/Microsoft Copilot, the maintained custom proxy list, `assettolab.ru`, and Apple Intelligence / Private Cloud Compute endpoints.
4. Apple, Google core services, and GitHub core services are `DIRECT` through maintained Blackmatrix7 rule sets.
5. `.ru`, `.su`, `.рф`, FunPay, and `GEOIP,RU` are `DIRECT`.
6. Everything unmatched is `PROXY`.

OpenAI/ChatGPT, Claude, Grok/xAI, Perplexity, Microsoft AI, and other AI/niche services that are not part of a broad DIRECT family intentionally fall through to the default proxy. This avoids unnecessary extra rule sets while preserving access.

Generic shared CDN networks such as Cloudflare, Fastly, Akamai, AWS/CloudFront, and similar infrastructure are deliberately not routed DIRECT as a whole because blocked and niche services share them.

The config intentionally keeps:

- `udp-policy-not-supported-behaviour = DIRECT`
- `block-quic = always-allow`
- IPv6 disabled
- system DNS for DIRECT traffic and DoH through the proxy for proxied traffic

## Private material

Do not commit proxy credentials, subscription URLs, API keys, authentication tokens, private keys, `ca-p12`, or `ca-passphrase` values.

Keep the MITM CA local to Shadowrocket. The public config only enables MITM and does not contain CA private material.
