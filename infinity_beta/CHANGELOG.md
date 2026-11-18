# Changelog

## 14.0-beta10
Big libraries, music on a NAS, and nearly every kind of music file.

**Highlights**
- Built for big libraries: with 200,000 tracks and more, Albums, Artists, artist pages, playlists and Focus open right away — on a small Home Assistant box too. A ♡ no longer makes the lists load again.
- Music on a NAS: the first scan reads several files at once and finishes several times sooner, and opening Infinity Core no longer spends minutes checking a large network folder.
- Plays nearly every kind of music file: Monkey's Audio (APE), Ogg Vorbis, Opus, WMA, TTA, TAK, Musepack, Shorten, AC-3, DTS and Matroska audio — the same on Mac, Windows and Linux. Settings › Library › Supported formats lists what your computer plays.

**New**
- PEQ: import a ParametricEQ .txt (AutoEQ, Equalizer APO) on the PEQ page — the Import button, or drop the file on the editor. With a DAP as the output, the DAP imports the file itself.
- Library: two copies of one album in different folders are two versions, each with a name — its folder's ("Vinyl", "Japan · 24-96") or its media, country and label. An album with only one of its songs here is no longer called a Single or EP.
- Settings in 9 sections instead of 12: Library holds your music folders, scan and maintenance; Services has everything Qobuz and TIDAL; Troubleshooting sits in About.

**Improvements**
- Smart playlists on the phone open at once, however many tracks they match.
- Home Assistant and Docker: Infinity Core uses far less memory after you browse a big library.
- WMA, AC-3, MP2 and other lossy files are labelled Lossy.
- The volume slider follows your finger smoothly, on the computer and on the phone.
- Qobuz and TIDAL playlist rows: square covers unless most are wide, and My Qobuz in the same order as My TIDAL.
- Signing out of Qobuz or TIDAL also takes that account's ♡ off your artists.

**Fixes**
- FLAC files with ID3 tags in front of the music said "not a FLAC file" and did not play. They play now.
- A file that cannot be opened — a network folder that is away — says so, instead of "not a FLAC file".
- Ogg, Opus and APE files no longer sit in the library greyed out.
- A DAP on Infinity Link: when its listener picks another album on the DAP itself, Infinity Core follows within a second or two (it kept showing the old one).
- TIDAL: tracks on a mix page link to their artist, and a "More" list no longer stays blank.
- Tag editor: a file it rewrites keeps its permissions.
