# Cuetide — releases and support

Cuetide is an independent companion for Apple Music on macOS. This repository is for release installers, release notes, bug reports and feature requests. The application source stays in a separate private repository; no application source or private source history is hosted here.

- [Releases](https://github.com/Nariiius/cuetide-releases/releases)
- [Report a bug or suggest an improvement](https://github.com/Nariiius/cuetide-releases/issues/new/choose)
- [Roadmap](ROADMAP.md)
- [Private security and privacy contact](SECURITY.md)

## Release availability and requirements

This repository is **private during preparation**. It will become public only after Narius approves. **v1.0.0** is the planned first public release, based on a pinned snapshot of the source repository’s `main` branch. There is no public installer yet.

Licence terms have not been selected. No `LICENSE` file or licence grant is supplied by this repository; the licence decision remains with Narius before distribution.

Check **Releases** for availability. If there is no published release with a matching `.dmg` and `.dmg.sha256`, there is no public installer to download here yet. A local build or draft release is not a public release.

- Target platform: macOS 26 or newer and Apple’s Music app. Native release preparation has been exercised on Apple silicon; Intel compatibility is not established for v1.0.0. Release-specific verification will be recorded when an installer is attached.
- Cuetide is currently free. Apple Music streaming and account features may require Apple's subscription and authorisation, separately from Cuetide.
- The intended initial distribution uses ad-hoc signing, not a Developer ID certificate, and is not notarised. MusicKit-only catalogue/account features may be unavailable without a matching enabled App ID; local-library controls use a separate path.

## Download and first launch

1. On the published release page, read the release notes and download its matching DMG and SHA-256 file. Do not use installers attached to issues or from unknown mirrors.
2. In Terminal, from the folder containing both files, run `shasum -a 256 -c` followed by the downloaded checksum filename. The result should say `OK`. A checksum checks file integrity, **not publisher identity, malware safety or notarisation**. Stop if verification fails.
3. Open the DMG and drag Cuetide into Applications, then try opening it.
4. If macOS says it cannot verify the developer or check the app for malware, click **Done**. Only if you trust the download, open **System Settings → Privacy & Security → Open Anyway** for Cuetide, authenticate, and confirm. See [Apple's current instructions](https://support.apple.com/en-us/102445).

If macOS reports malware, damage, or provides no per-app override, stop and report the problem privately. Do not disable Gatekeeper, remove quarantine attributes, or bypass a malware warning.

Grant permissions only for features you use: Automation allows control of Music, and system-audio recording enables the waveform. Updates to an ad-hoc build can require renewed permission approval. Do not delete your library or reset unrelated applications' permissions to troubleshoot.

## Privacy and support

Audio processing and on-device AI filtering run locally. Track metadata can still be sent directly to Apple, LRCLIB and ReccoBeats for artwork, lyrics or enrichment, and to GetSongBPM if you configure your own key; those providers receive network information such as your IP address. There is no developer-run app telemetry service.

Issues are currently restricted to people with repository access. **Issues and attachments may become public and indexed when this repository becomes public.** Share only the app/macOS version and a minimal reproduction. Redact screenshots and examples; never post API keys, account details, full music-library exports, unredacted logs or private listening information. Do not post security vulnerabilities or deletion requests in issues.

For private security reports, privacy/deletion questions, or a report that cannot be safely redacted, contact **Narius** at **nariushere@gmail.com**. See [reporting guidance](SECURITY.md). GitHub operates the issue and download platform under its [privacy statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement); we cannot guarantee removal of copies held by third parties.

## Roadmap and affiliation

The [roadmap](ROADMAP.md) is intentionally small. Feature requests are suggestions, not delivery promises; there are no announced feature dates.

Cuetide is operated by Narius in Victoria, Australia. It is an independent application and has not been authorised, sponsored or otherwise approved by Apple Inc. Apple, Apple Music, Mac and macOS are trademarks of Apple Inc., registered in the U.S. and other countries and regions.
