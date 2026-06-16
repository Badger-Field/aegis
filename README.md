<p align="center"><img src="logo.png" alt="Aegis" width="540"></p>

# Aegis

Kodi 21 (Omega) addon delivery for the Aegis build. Source lives in a
separate (private) repository; this repo carries only the signed release
payload that Kodi pulls.

## Before you start

Kodi blocks installs from unknown sources by default. Turn it on once:
**Settings → System → Add-ons → Unknown sources → On** (acknowledge the warning).

## Install

**1. Add the source.**
Settings → File Manager → Add Source → `<None>`
- Path: `https://badger-field.github.io/aegis/`
- Name: `aegis`
- OK

**2. Install the repository addon (one-time).**
Settings → Add-ons → Install from zip file → `aegis` → `zips/` → `repository.aegis/` →
`repository.aegis-0.1.0.zip`. Wait for the *Aegis Repository installed* toast.

**3. Install Aegis Build from the repository.**
Settings → Add-ons → Install from repository → **Aegis Repository** → **Video add-ons** →
**Aegis Build** → *Install*. Kodi will prompt to install the dependencies
(`script.module.aegis.netguard`, `script.module.aegis.vault`,
`script.module.aegis.tvhub`, `script.module.requests`) — accept.
Wait for the *Aegis Build installed* toast.

**4. Install the first-run service.**
Install from repository → Aegis Repository → **Services** → **Aegis First Run** → *Install*.
This addon runs the consent + Real-Debrid OAuth wizard at Kodi startup.

**5. (Optional) Install the skin.**
Install from repository → Aegis Repository → **Look and feel** → **Skin** → **Aegis Skin** →
*Install*. After install, Kodi asks *Switch to the new skin?* → **Yes**.

**6. Restart Kodi.**
Power → Exit, then relaunch. On the next startup, *Aegis First Run* triggers the
wizard: consent → debrid provider → Real-Debrid OAuth device-flow (5-min code at
<https://real-debrid.com/device>). After it finishes, you're done.

Launch from the home screen: **Add-ons → Video add-ons → Aegis Build**.

### Optional extras (install any time, same as step 4)

- **Umbrella** (`plugin.video.umbrella`) — Real-Debrid scraper. Video add-ons.
- **Aegis TVE** (`plugin.video.aegis.tve`) — TV-Everywhere providers. Video add-ons.

### Updates

Settings → Add-ons → check the Aegis Repository periodically — Kodi installs new
versions in place. Last 3 versions of each addon are retained here for
rollback if needed.

Direct link to the current repository zip: <https://badger-field.github.io/aegis/zips/repository.aegis/repository.aegis-0.1.0.zip>

## What's in this repo

- `addons.xml` / `addons.xml.gz` — Kodi addon manifest with per-addon SHA256.
- `zips/<addon-id>/<addon-id>-<version>.zip` — built addon payloads.
- `index.html` at each directory — Apache-autoindex-style listing so Kodi's HTTP vfs
  can browse the repo (GitHub Pages doesn't auto-list directories).

All zips are produced by a deterministic build from pinned upstream commits.
