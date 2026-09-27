# Shadowrocket

Public Shadowrocket configuration used from GitHub.

## Config URL

https://raw.githubusercontent.com/sevenracin/dotfiles/main/networking/shadowrocket/shadowrocket.conf

Add this URL to Shadowrocket as a remote configuration. The config contains the same URL in `update-url`, so later edits can be pulled without recreating the configuration.

## Private material

Do not commit proxy credentials, subscription URLs, API keys, authentication tokens, private keys, `ca-p12`, or `ca-passphrase` values.

Keep the MITM CA local to Shadowrocket. The public config only enables MITM and does not contain CA private material.
