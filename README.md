# Cuetide

An independent Apple Music companion for macOS: a left-edge waveform, floating player, live queue, library filters and lyrics.

[Releases](https://github.com/Nariiius/cuetide-releases/releases) · [Bugs & ideas](https://github.com/Nariiius/cuetide-releases/issues/new/choose) · [Small roadmap](ROADMAP.md) · [Private contact](SECURITY.md)

## Download

**[Download Cuetide 1.0.0](https://github.com/Nariiius/cuetide-releases/releases/download/v1.0.0/Cuetide-1.0.0.dmg)** · [SHA-256 checksum](https://github.com/Nariiius/cuetide-releases/releases/download/v1.0.0/Cuetide-1.0.0.dmg.sha256) · [Release notes](https://github.com/Nariiius/cuetide-releases/releases/tag/v1.0.0)

This repository hosts official app downloads and support, not the private application source or its history.

- Requires **macOS 26+ and Apple Music**. Initial packaging targets Apple silicon; Intel compatibility is not verified.
- Cuetide is free. Apple Music services can require a separate account and subscription.
- This build is **ad-hoc signed, not Developer ID signed or notarized**. MusicKit catalog/account features may be unavailable; local Music.app control is a separate integration.
- **Proprietary freeware:** use the app for free, including ordinary workplace use. Backup copies and sharing official download links are welcome. Redistribution, repackaging, resale or modification needs permission, subject to applicable law and third-party rights. See the short [licence](LICENSE). The private source is not licensed for reuse.

## Install and update

Download the matching DMG and checksum from **Releases**, not an issue attachment or unknown mirror. From the folder containing both files:

```sh
shasum -a 256 -c Cuetide-1.0.0.dmg.sha256
```

Continue only if the matching DMG reports `OK`. A checksum checks integrity, **not publisher identity or malware safety**. Open the DMG, drag Cuetide into Applications, eject the image and launch the installed copy. Look for its menu-bar icon and screen-edge panel rather than a Dock window.

If macOS blocks the trusted unsigned app, use **System Settings → Privacy & Security → Open Anyway** for Cuetide, if offered, then authenticate and confirm. [Apple's instructions](https://support.apple.com/en-us/102445). Stop if macOS reports malware, damage or offers no genuine per-app override. Do not disable Gatekeeper or strip quarantine attributes.

Grant only the permissions you need: **Automation → Music** for library/playback actions; **System Audio Recording** for the local waveform; optional **Accessibility** for mirroring Music's pins and opening its AirPlay picker. MusicKit authorization is separate and does not fix missing signing/provisioning.

For an update, quit Cuetide, verify the new release's matching checksum and replace the Applications copy. Ad-hoc updates **may** require renewed permissions; review the installed copy in System Settings. Do not reset unrelated apps' permissions. Private Apple interfaces can change, so a permission reset cannot fix every queue or lyrics failure.

## Playlists and privacy

Filtering replaces the contents of Cuetide's managed **`Filter: Current`** playlist, tracked by persistent ID—not just its name. **Add to Playlist** adds tracks to the existing playlist you select. Uninstalling does not undo Music-side changes. Keep backups of valuable playlists.

Audio analysis and AI-assisted filtering run locally. Cuetide does not use your microphone, save/upload the audio stream, or operate an app account/backend or developer telemetry service. It does make direct HTTPS lookups: **Apple** for artwork/catalog information, **LRCLIB** for lyrics, **ReccoBeats** for track features, and optional **[GetSongBPM](https://getsongbpm.com)** with your own API key. Providers receive relevant track metadata and your IP address; requests are **not anonymous**. Missing/stale feature metadata can be enriched automatically on library load or refresh.

## Remove Cuetide

Quit Cuetide and move `/Applications/Cuetide.app` to Trash. Local data remains unless you remove it separately.

<details>
<summary>Optional: erase only Cuetide's local data</summary>

In `~/Library/Application Support/Music/`, remove only confirmed Cuetide files:

- `library_cache.json`
- `track_features.sqlite3`
- `track_tags.sqlite3` — deleting this loses teachings and corrections
- `getsong_bpm_cache.sqlite3`

For each listed SQLite file, include its exact matching `-wal`, `-shm` and `-journal` sidecars, if present. Known schema backups are `track_tags.sqlite3.pre-schema-v3.sqlite3` and `track_features.sqlite3.pre-schema-v3.sqlite3`; include their exact matching sidecars and other confirmed Cuetide backups/exports only if no longer needed. Keep databases and sidecars together when backing up.

Networking stores may remain in `~/Library/Caches/com.narius.cuetide/` and `~/Library/HTTPStorages/com.narius.cuetide/`. With the app quit, move only those exact app directories to Trash—not their shared parents.

Optionally run `defaults delete com.narius.cuetide` to reset settings, pins, the managed-playlist identifier and any GetSongBPM key stored in preferences. UserDefaults is not a secrets vault. Remove separately configured environment keys there too; this does not revoke a provider key.

If you used the earlier Library panel demo, its pin cache can be imported again. With Cuetide quit, also remove only the legacy keys, if present: `defaults delete local.cuetide.library-panel-demo.pins music.sidebar.pins` and `defaults delete local.cuetide.library-panel-demo.pins music.sidebar.pins.date`. A missing key needs no action.

**Never delete the entire `~/Library/Application Support/Music/` folder, your Music library or Apple's lyric caches. No broad wildcard deletion.** Leave uncertain files alone. Check backups before emptying Trash. Removing preferences does not remove the managed playlist or undo other playlist changes.

</details>

## Bugs, ideas and private requests

Use **Bugs & ideas** for a minimal, redacted reproduction and the Cuetide/macOS version. **Issues and attachments are public and may be indexed or copied.** Never post keys, account details, full libraries, private listening information or unredacted logs.

Email **[nariushere@gmail.com](mailto:nariushere@gmail.com)** for security reports, sensitive bugs or privacy/access/deletion requests. Requests concern records Narius controls, not remote erasure of your Mac or providers' records. GitHub handles its platform data under its [privacy statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement).

The roadmap is intentionally small; suggestions are not delivery promises.

## About

Made by **Narius, Victoria, Australia**. Cuetide is provided “as is” and “as available” to the extent permitted by law. **Nothing here excludes rights or remedies that cannot lawfully be excluded, including under the Australian Consumer Law.** The [freeware licence](LICENSE) covers the app binary, not the private source or third-party content. There is no promise of future compatibility.

Cuetide is not affiliated with, endorsed, sponsored or approved by Apple Inc. Apple, Apple Music, Mac and macOS are trademarks of Apple Inc., registered in the U.S. and other countries and regions. Provider content retains its own rights; API access or a credit does not grant blanket music, artwork or lyric rights.
