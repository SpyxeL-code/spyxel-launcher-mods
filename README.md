# spyxel-launcher-mods

Mods auto-update source for [Spyxel Launcher](https://github.com/SpyxeL-code/Spyxel-Launcher).

The launcher fetches [`manifest.json`](manifest.json) at each launch and syncs the
user's `mods/` folder to match. SHA256 of each file is verified after download.

`manifest.json` is signed (Ed25519) — its signature lives in
[`manifest.sig`](manifest.sig). The launcher embeds the matching public key and
refuses any manifest whose signature does not verify. A compromised copy of this
repo therefore cannot push malicious mods without the (offline) private key.

- MC version: `1.21.11`
- Loader: `fabric`
- Mods: 35
- Last update: 2026-06-07

## Privacy

Every request is an anonymous HTTPS GET. No user data, no account info, no
User-Agent containing app version or OS info. GitHub's CDN sees the client IP,
nothing else.

## How to update

1. Drop new `.jar` versions in `mods/`, delete obsolete ones.
2. Regenerate `manifest.json` (run `npm run publish-mods` in the launcher repo,
   it overwrites this folder).
3. Commit & push.
