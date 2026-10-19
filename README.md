# Cuetide

An independent Apple Music companion for macOS: a left-edge waveform, floating player, live queue, library filters and lyrics.

[Releases](https://github.com/Nariiius/cuetide-releases/releases) · [Bugs & ideas](https://github.com/Nariiius/cuetide-releases/issues/new/choose) · [Small roadmap](ROADMAP.md) · [Private contact](SECURITY.md)

## Download

**[Download Cuetide 1.0.0](https://github.com/Nariiius/cuetide-releases/releases/download/v1.0.0/Cuetide-1.0.0.dmg)** · [Release notes](https://github.com/Nariiius/cuetide-releases/releases/tag/v1.0.0)

This repository hosts official app downloads and support, not the private application source or its history.

- Requires **macOS 26+ and Apple Music**. Initial packaging targets Apple silicon; Intel compatibility is not verified.
- Cuetide is free. Apple Music services can require a separate account and subscription.
- This build is **ad-hoc signed, not Developer ID signed or notarized**. MusicKit catalog/account features may be unavailable; local Music.app control is a separate integration.
- **Proprietary freeware:** use the app for free, including ordinary workplace use. Backup copies and sharing official download links are welcome. Redistribution, repackaging, resale or modification needs permission, subject to applicable law and third-party rights. See the short [licence](LICENSE). The private source is not licensed for reuse.

## Install and update

1. **Download** the DMG from the official link above.
2. **Open** the DMG and drag **Cuetide** into **Applications**.
3. Eject the DMG and **open Cuetide from Applications**. Look for its menu-bar icon and screen-edge panel rather than a Dock window.

This free release is ad-hoc signed, without an Apple Developer ID or notarisation. If macOS blocks a copy you trust, use **System Settings → Privacy & Security → Open Anyway** for Cuetide, if offered, then authenticate and confirm. [Apple's instructions](https://support.apple.com/en-us/102445). Stop for malware/damage warnings or if no genuine per-app override is offered; do not disable Gatekeeper or strip quarantine attributes.

<details>
<summary>Optional: verify the download's SHA-256 checksum</summary>

Download the matching [checksum file](https://github.com/Nariiius/cuetide-releases/releases/download/v1.0.0/Cuetide-1.0.0.dmg.sha256) into the same folder as the DMG. From that folder, run:

```sh
shasum -a 256 -c Cuetide-1.0.0.dmg.sha256
```

The matching DMG should report `OK`. If it does not, stop and download the matching files again. A checksum checks file integrity, **not publisher identity or malware safety**.

</details>

Grant only the permissions you need: **Automation → Music** for library/playback actions; **System Audio Recording** for the local waveform; optional **Accessibility** to refresh Music's live Pins, open native pins not matched to a library song/playlist, and open Music's native AirPlay picker. Cached pins matched to library songs/playlists, live queue actions, AutoPlay and AutoMix do not require Accessibility. MusicKit authorization is separate and does not fix missing signing/provisioning.

For an update, quit Cuetide and replace the Applications copy with the new release. Checksum verification is optional. Ad-hoc updates **may** require renewed permissions; review the installed copy in System Settings. Do not reset unrelated apps' permissions.

## What you can do

- **Keep music at the screen edge.** See an audio-reactive waveform and hover to open the floating player, with artwork, playback controls, progress and volume.
- **Manage Up Next.** Jump to a queued song, remove it or reorder the live queue. AutoPlay and AutoMix reflect supported Music states; Cuetide does not run its own continuation engine.
- **Browse your library.** Open Pins, Playlists, Songs and Favourite Songs from the Library view.
- **Filter in plain language.** Explore your library with natural-language and mood filters, then use **Teach** to correct local classifications. Filtering uses local rules and Apple's on-device models when available.
- **Follow lyrics.** Show available local or LRCLIB lyrics; seek from a lyric line when synced lyrics are available.
- **Choose where sound plays.** Select a Mac playback output or open Music's native AirPlay picker. The picker needs Accessibility permission.
- **Adjust the glass.** Fine-tune frost, opacity, dark tint and artwork blur in Settings.

## Known issues and limitations

- [Performance problems — investigation #1](https://github.com/Nariiius/cuetide-releases/issues/1).
- [UI glitches — investigation #2](https://github.com/Nariiius/cuetide-releases/issues/2).

These reports are open for investigation; their causes and scope are not yet diagnosed.

Apple's private queue interfaces and local lyric-cache format can change with macOS/Music updates. A permission reset cannot repair an incompatible interface. MusicKit account/catalog features require Apple's authorisation and appropriate signing/provisioning; this ad-hoc build does not guarantee those features. Intel compatibility is not verified.

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
