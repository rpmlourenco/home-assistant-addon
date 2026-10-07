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
