# Changelog

## 14.0-beta27
Every recording of a song — yours, TIDAL's and Qobuz's — and one artist page for every artist.

**Highlights**
- Recordings, as Roon counts them: each song on an album page shows how many recordings of it there are — in your library and on TIDAL and Qobuz — and the song's page lists them all: who performed it, on which album, where it is, with filters and sorting. Other songs that only share the title are left out.
- One artist page for every artist: an artist from a TIDAL or Qobuz search opens the same page as one in your library, with the albums from your library, TIDAL and Qobuz together. Discography shows All · Your library · TIDAL · Qobuz.
- One search: your library, TIDAL and Qobuz in one list, your own music first, with a From filter.
- Private session: for 1 to 12 hours nothing you play is kept — not in History, your stats, suggestions, Autoplay, AI mixes or Last.fm. A DAP on Infinity Link follows.
- Sound per output: each output remembers its own Infinity DSP, upsampling, EQ, PEQ and listening profile.
- Dynamic range (DR14), measured the way Infinity OS measures it: on albums, in Now Playing and as a column in Tracks. FLAC, WAV and DSF files get it in their tags so your DAP shows it too — or keep it in the library only.

**Improvements**
- Album versions: one card per album with how many versions you have. The Versions tab shows where each one is stored, lets you choose the primary version, and takes a version out of the group (Remove from group).
- Multi-disc albums: a header for each disc with its title; CD1 / CD2 folders of one album are one album. A disc with a title of its own (a box's demos disc) stays an album of its own.
- Compilations without an album artist are one album again (Various Artists, or the artist of most of the tracks).
- Album rows say who performed a song when there is a guest (a duet, a featured artist). Settings › Credits under each track shows the writers too, or nothing.
- The artist page is one long page: popular tracks beside the biography, the latest release, the whole discography, similar artists. Its buttons as in Roon: Play ▾ (Shuffle, Start radio), ♡, Listen later.
- The album page ends with similar artists.
- Playlist files: .m3u / .m3u8 files in your music folders show up as playlists, and your playlists can be kept as .m3u8 files too.
- Music folders: an Add / Edit window with folders to ignore, how often a network share is read again, and the scan's progress.
- In a long list, type a letter to jump to it. Tracks sort by quality: DSD, Hi-Res, CD, then lossy.
- Using your home Infinity Core away from home: the app reaches it through Tailscale by itself, and Settings says so.

**Fixes**
- Qobuz artist pages no longer list other artists' records, or the same album under Albums, Singles, Live and Compilations.
- Two copies of an album in two folders — one with disc numbers, one without — are two versions again, not one album with Disc 1 twice.
- A NAS's hidden snapshot folders (.zfs/snapshot) no longer get into the library when files change.
- Clicking a song no longer squeezes its row.
- After an update, the app always opens the new version of its pages.
- After Split artist, each artist's own picture shows at once.
- The app no longer slides off the window's left edge.
