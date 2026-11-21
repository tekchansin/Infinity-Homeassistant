# Changelog

## 14.0-beta19
Manage your music files, tidy duplicates, and AI with your own key.

**Highlights**
- Folders is a file manager now: drag files in to upload, download a file or a folder as .zip, copy and move (Copy to… / Move to…, or drag onto a folder), new folder, rename, delete. Pick a file to see everything about it — format, tags, cover, loudness, where it is in your library. On Mac and Windows deleting goes to the Trash; on a server it asks first, then deletes for good. Not over Remote access.
- Duplicates: Settings › Library Health › Duplicates finds albums kept in more than one folder and songs stored twice. Keep the copy you want and remove the rest — plays, ♡ and playlists move to the one you keep. A DAP's own files too.
- AI with your own key (beta): Settings › AI. Connect OpenRouter, Anthropic or an AI on your own network, then make a playlist from a few words, get what to play next, translate lyrics and tidy an album's tags. Nothing is sent until you set it up; What AI sees lists what each feature sends, and AI activity shows every request.

**Improvements**
- A new Home: what plays now and today's listening time, then a listening diary — one row per album you sat down with — beside your library, the last 7 days and who you played most. A DAP's page and the phone's Home match, and a fresh library gets Not heard yet, Just added and Album of the day.
- Library Health (Settings): Covers finds albums with no cover, a small or not-square one, or the same picture on several albums. Find better covers searches MusicBrainz, iTunes, Qobuz, TIDAL and Kugou and puts the cover you pick into every song of the album, with one Undo. Search on COV opens covers.musichoarders.xyz for many more stores.
- Name your Infinity Core: Settings › General › Name — DAPs, phones and other computers show it.
- Tag editor: a Location column (your DAP or this computer), Show in Folders, and Fix tags.
- Updates: Settings › About also shows this app's own update while it uses another Infinity Core. A Docker copy now updates itself; Home Assistant and Umbrel copies are updated by their store.

**Fixes**
- Copy from a DAP: songs with very long names (for example Thai titles listing every featured singer) now come across; Sync to DAP and phone Downloads handle them too.
- Lyrics: when none are found, it tries once more without the edition and guest words in the title.
- History keeps plays of songs that were moved or re-read since.
