# Changelog

## 14.0-beta28
Everyone at home gets a profile of their own — their own favourites, history and music at the same time — and your computer's speakers play from anywhere.

**Highlights**
- Profiles: each person at home has their own favourites, Listen Later, History, Home, playlists, Last.fm and ListenBrainz, and TIDAL / Qobuz (the home's sign-in or their own). Up to four people play their own music at once, each on their own output; an output in use shows who is listening and stays theirs until they stop. A new device asks Who's listening? once; switch from the top bar. Settings › Profiles adds and removes profiles and exports or imports a profile's data.
- Your speakers from anywhere: with Link Anywhere on, the speakers this Mac shares play from your Infinity Core at home while you are away — 20 seconds buffered, lossless FLAC on the way.
- Background work: the Core's upkeep — the daily backup, tidying the library, DR of new tracks, artist and album information — runs at night (01:00–05:00) or when nothing plays, and stops as soon as music plays. Settings › Library & Storage › Background work.

**Improvements**
- Your Home Core away from home in one tap: when it is on Link Anywhere, the app offers to turn it on for this Mac too — one Tailscale sign-in, then Home answers from anywhere (also in Settings › Core in use).
- ListenBrainz: send what you play to your ListenBrainz account (Settings › Services › Scrobbling).
- No output: tap the output in use again to disconnect it; the music waits where it was.
- Explicit songs and albums show a small E — from your files' tags, TIDAL and Qobuz.
- Settings › Library & Storage: your folders with their track counts, Import, Background work, Maintenance and Backups in one place. Services comes in three parts: Streaming, Scrobbling and Backup (Google Drive), with In My Library in each service's box.
- The library opens on the tab you used last. Every album has Show in Folders, a DAP's album too.
- TIDAL and Qobuz pages open at once from what was seen before, then refresh.
- DR (dynamic range) is kept in the library only; your files are no longer written.
- A lighter sidebar.

**Fixes**
- Quitting Infinity Core, or the computer going to sleep, no longer hands its queue to a DAP that is playing its own music.
- Swiping back no longer happens on a fast scroll up or down.
- Infinity Core in Docker or on a NAS without a time zone of its own follows your app's time zone, so its night is your night.
