# Shadowrocket

Public Shadowrocket configuration used from GitHub.

## Config URL

https://raw.githubusercontent.com/sevenracin/dotfiles/main/networking/shadowrocket/shadowrocket.conf

Add this URL to Shadowrocket as a remote configuration. The config contains the same URL in `update-url`, so later edits can be pulled without recreating the configuration.

## Routing policy

The profile is intentionally **proxy by default** for unknown and niche services, but known-safe traffic is routed `DIRECT` for native speed.

Proxied traffic now uses the `FAST-EU` `url-test` group instead of Shadowrocket's plain `PROXY` policy. The group automatically tests nearby EU nodes every 5 minutes and picks the lowest-latency available match with a 20 ms switching tolerance. It currently matches Finland, Estonia, Latvia, Lithuania, Poland, Sweden, Germany, the Netherlands, Czechia, Denmark, and Austria, using country names, common city names, Russian names, and flags. Special nodes labelled `МОСТ`, `ТОРРЕНТ`, or M-number variants are excluded.

All protocols exposed by matching subscription nodes participate. Shadowrocket `url-test` measures request latency/availability rather than sustained download throughput, so the configuration intentionally does not hard-code a preferred protocol. A fast Hysteria2/TUIC/VLESS/etc. node can win naturally if it performs best on the current connection.

Rule order is important:

1. LAN and Tailscale are `DIRECT`.
2. Advertising is rejected.
3. Narrow exceptions that need a foreign IP use `FAST-EU` before any broad direct category can match them. This includes OpenAI, Gemini, YouTube, GitHub/Microsoft Copilot, Medium, JetBrains AI/Grazie, the maintained custom proxy list, `assettolab.ru`, and Apple Intelligence / Private Cloud Compute endpoints.
4. Apple, Google, GitHub, Developer, and Game aggregate families are `DIRECT` through maintained Blackmatrix7 rule sets.
5. `.ru`, `.su`, `.рф`, FunPay, and `GEOIP,RU` are `DIRECT`.
6. Everything unmatched uses `FAST-EU`.

Generic shared CDN networks such as Cloudflare, Fastly, Akamai, AWS/CloudFront, and similar infrastructure are deliberately not routed `DIRECT` as a whole because blocked and niche services share them.

The config intentionally keeps:

- `udp-policy-not-supported-behaviour = DIRECT`
- `block-quic = always-allow`
- IPv6 disabled
- system DNS for DIRECT traffic and DoH through the proxy for proxied traffic

## Private material

Do not commit proxy credentials, subscription URLs, API keys, authentication tokens, private keys, `ca-p12`, or `ca-passphrase` values.

Keep the MITM CA local to Shadowrocket. The public config only enables MITM and does not contain CA private material.
