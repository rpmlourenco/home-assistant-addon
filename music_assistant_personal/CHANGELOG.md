## 2.10.4.dev8

- Separate local tracks from different album releases during import, preserving the official matching behaviour for other providers.
- Preserve MusicBrainz recording and release-track identifiers according to FLAC, MP3, M4A and APEv2 tag conventions.
- Include album version metadata in full and summary track listings and queue media items.
- Remove the dev7 album context restrictions from queue creation, stream selection, cache reuse and retries.
- Validate the installed image and local edition regression tests before publishing ARM64 images.

Existing merged library tracks are not automatically split. Updating or rescanning an unchanged file can retain its existing mapping and library ID. Existing playlists continue referencing their current items; they are not automatically rewritten to select another edition.

Album version metadata is exposed to clients. Its display in each playlist or now-playing view depends on the client. Matching to streaming providers keeps the official behaviour and does not guarantee the same mastering as the local release.
