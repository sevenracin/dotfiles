# Shadowrocket

Public Shadowrocket configuration used from GitHub.

## Config URL

https://raw.githubusercontent.com/sevenracin/dotfiles/main/networking/shadowrocket/shadowrocket.conf

Add this URL to Shadowrocket as a remote configuration. The config contains the same URL in `update-url`, so later edits can be pulled without recreating the configuration.

## Routing policy

The profile is intentionally **proxy by default** for unknown and niche services, while known-safe traffic is routed `DIRECT` for native speed.

The design is deliberately small: explicit proxy rules are only kept when they override a later `DIRECT` family or `GEOIP,RU`. Services that would already fall through to `FINAL,FAST-EU` do not get redundant rule sets.

### Proxy selection

`FAST-EU` is a stability-first `url-test` group. It tests a small nearby-EU pool every 30 minutes with a 3 second timeout and a 50 ms switching tolerance. The current pool covers Finland, Poland, Sweden, Germany, the Netherlands, and Denmark. Russian/Moscow-labelled and special-purpose nodes are explicitly excluded even if their names also contain an EU label.

All matching protocols may compete. Shadowrocket `url-test` measures request latency/availability, not sustained throughput, so protocol type is not hard-coded.

`GOOGLE-AI` is deliberately different: it is a manual `select` group populated from normal non-Russian subscription nodes. Google AI has aggressive VPN/risk checks, so use one stable exit and avoid automatic node rotation. After refreshing the config, open the `GOOGLE-AI` policy group and select the specific server you want Gemini/Google AI to use.

### Google AI coverage

Google AI traffic is separated before the broad Google `DIRECT` rule. The local rules mirror the current upstream `google-deepmind` service family and cover Gemini, DeepMind, Generative Language API, AI Studio, NotebookLM, Jules, Google AI Labs/Flow, Gemini Code Assist, Android Studio Gemini, Opal, Antigravity, and Stitch.

The older Blackmatrix7 `Gemini.list` is not used for this group because it is much smaller and misses several newer Google AI products.

### DNS

DIRECT traffic uses the system resolver. Proxied traffic uses one direct Cloudflare DoH resolver with Google DoH and the system resolver as fallbacks.

DNS is intentionally **not sent through `#proxy`**. Shadowrocket's `#proxy` DNS syntax uses the current default proxy node, which can make DNS reliability independent from the node selected by `FAST-EU`. Keeping DNS outside the proxy path avoids that extra failure point.

Apple/iCloud/App Store hostnames are also explicitly resolved with the system resolver.

### Rule order

1. LAN and Tailscale are `DIRECT`.
2. Narrow exceptions that would otherwise be caught by a later direct rule or Russian GEOIP use `FAST-EU`. This includes OpenAI, GitHub Copilot, Discord, Medium, JetBrains AI/Grazie, the small maintained Misha custom-proxy list, `assettolab.ru`, and Apple Intelligence / Private Cloud Compute endpoints.
3. Google AI uses the dedicated manual `GOOGLE-AI` group before Google core can match it.
4. YouTube explicitly uses `FAST-EU` before Google core. This prevents the native app from being split between proxied YouTube domains and Google API/video infrastructure such as `youtubei.googleapis.com`, `googlevideo.com`, and GVT hosts.
5. Apple core traffic is `DIRECT` through explicit critical suffixes plus Blackmatrix7 `Apple_Domain` and `Apple` sets.
6. Google core, GitHub core, Developer, and Game aggregate families are `DIRECT`.
7. `.ru`, `.su`, `.рф`, FunPay, and `GEOIP,RU` are `DIRECT`.
8. Everything unmatched uses `FAST-EU`.

Microsoft Copilot, Claude, Grok/xAI, Perplexity, and other foreign services that are not part of a broad DIRECT family intentionally fall through to the default proxy instead of carrying redundant explicit proxy lists.

## Why there is no giant ad list

The base routing profile intentionally does **not** load Blackmatrix7 `Advertising_Domain.list`. That file is several megabytes and expands to hundreds of thousands of rules, dwarfing the rest of the routing table. Ad blocking is better kept in dedicated Shadowrocket modules/content blockers rather than making every connection traverse an enormous base routing database.

## Notes

The config intentionally keeps:

- `udp-policy-not-supported-behaviour = DIRECT`
- `block-quic = always-allow`
- IPv6 disabled
- system DNS for DIRECT traffic
- MITM enabled, while CA private material stays local

## Private material

Do not commit proxy credentials, subscription URLs, API keys, authentication tokens, private keys, `ca-p12`, or `ca-passphrase` values.

Keep the MITM CA local to Shadowrocket. The public config only enables MITM and does not contain CA private material.
