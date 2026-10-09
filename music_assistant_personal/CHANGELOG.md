## 2.10.5.dev6

- Reduce the global metadata update interval from 30 to 3 seconds.
- Keep provider-specific limits unchanged, including LRCLIB, and retain existing
  settings and audio analysis results; no library reanalysis is required.
- Validate metadata regressions and the installed throttle before publication.

## 2.10.5.dev5

- Combine Similar Tracks from active providers, including Last.fm and Sonic
  Similarity, instead of keeping only the first provider's results.
- Interleave provider rankings, remove duplicates and the seed track, and honor
  the total result limit. A failed provider does not suppress healthy results.
- Use the same combined recommendations for radio continuation and Auto/Similar
  autoplay. Library/Playlist autoplay modes and recent/queued-track filters stay
  unchanged.
- Include the post-dev4 typing corrections and validate similarity/autoplay/radio
  regressions, installed-image merge behavior, and the global mypy gate.
- Keep existing analysis results and settings; no library reanalysis is required.

## 2.10.5.dev4

- Include the shared analysis models, lazy provider exports and Smart Fades helpers
  required to keep the server image consistent with the offline analysis code.
- Include offline CUDA support for Smart Fades and Sonic; Home Assistant continues
  to use CPU defaults, and existing sidecars do not require recomputation.
- Validate standalone imports in the installed image and extend Smart Fades
  regression checks before publishing the ARM64 image.
- Maintain the server fork on main, with Git tags and matching image/add-on versions.

## 2.10.5.dev3

- Import precomputed audio-analysis results from gzip JSON `.lda` files alongside local FLAC tracks during background scans.
- Validate the source audio fingerprint and each provider's algorithm version, then persist valid results to SQLite.
- Calculate only missing providers on Home Assistant, with an enabled-by-default option to disable local background fallback.
- Support PC-side pre-analysis through FlacConverter's `analyze-audio` command, with incremental provider updates and atomic sidecar publication.
- Keep playback based on SQLite and preserve FLAC audio and tags.

## 2.10.5.dev2

- Let the nightly background audio-analysis scan run until all current candidate tracks are exhausted instead of stopping after a global four-hour budget.
- Retain the existing per-track timeout and provider hang safeguards.
- Ignore overlapping scheduled triggers while the same analysis task is already pending or running.

## 2.10.5.dev1

- Rebase the personal fork onto official Music Assistant 2.10.5 while preserving the custom behaviour from 2.10.4.dev9 and upstream fixes.
- Correct the background-analysis PCM format so decoded audio is not interpreted using the compressed source codec.

## 2.10.4.dev9

- Reject incompatible local import candidates before reading their files. Conflicting MusicBrainz release-track IDs and unrelated recordings no longer launch ffprobe or reload album/artist metadata during edition matching.
- Keep native source validation for ambiguous matches and preserve local edition separation.

## 2.10.4.dev8

- Separate local tracks from different album releases during import, preserving the official matching behaviour for other providers.
- Preserve MusicBrainz recording and release-track identifiers according to FLAC, MP3, M4A and APEv2 tag conventions.
- Include album version metadata in full and summary track listings and queue media items.
- Remove the dev7 album context restrictions from queue creation, stream selection, cache reuse and retries.
- Validate the installed image and local edition regression tests before publishing ARM64 images.

Existing merged library tracks are not automatically split. Updating or rescanning an unchanged file can retain its existing mapping and library ID. Existing playlists continue referencing their current items; they are not automatically rewritten to select another edition.

Album version metadata is exposed to clients. Its display in each playlist or now-playing view depends on the client. Matching to streaming providers keeps the official behaviour and does not guarantee the same mastering as the local release.
