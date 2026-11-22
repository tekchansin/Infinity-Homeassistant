# Changelog

## 14.0-beta20
Your music on a TV, a check for your setup, and smoother playback on small servers.

**Highlights**
- Displays: a TV, tablet or old laptop in the house shows what plays — the cover, the song and its lyrics, large. Settings › Displays: open the page on the TV and type the code it shows. A button beside the volume shows or stops it (it is there only when a display is on); Stop shows a clock until you press Play again.
- Check this Core (Settings › About): checks where Infinity Core runs, whether it finds your devices, whether it plays with real-time priority, and every device you play on — in plain words, with what to change (for Docker, the lines for docker-compose.yml). Copy report gives us everything we need to help.
- A new Home: Today's pick, rows you can scroll sideways with See all (New releases, Your mixes, Artists for you), Your listening, and Not for me to hide what you don't want. The listening diary moved to History.

**Improvements**
- Equalizer and PEQ changes are heard within a few seconds on this computer's DAC (it could take up to 17 seconds).
- Qobuz and TIDAL: the next song starts downloading before this one ends, so songs change without waiting.
- Home Assistant and Umbrel: music plays with real-time priority, covers are sent small (a 1.4 MB cover is about 15 KB on a phone's list), and the server writes far less to its disk.
- Make a playlist with AI: a new dialog with starters, close it and come back, Stop; AI is in the sidebar.
- Saved filters on every page (DAP pages too), and the last filter is kept.
- Queue: a menu on each song, and select several at once.
- New for you looks at 30 of your artists over the last 180 days.
- A phone's speaker is ready as soon as its app opens.
- Tablets get a sidebar from 800 px wide.
- Infinity Link devices: Forget a device you no longer use; Add by address finds a computer's shared devices without typing a port.
- Settings › Devices & Sharing shows each shared device's address, to add it by hand on a Core that does not find it.

**Fixes**
- A computer that played through "Play on this computer" before 14.0-beta16 moves to the device it shares, instead of staying "Not connected".
- Radio on Home Assistant, Umbrel and Docker: a station that stalled no longer froze Stop and Play.
- Qobuz and TIDAL: Next, Seek and Stop work at once even while the network stalls.
- Artist and album information no longer slows pages down while offline, and Qobuz and TIDAL pages that failed to load try again instead of staying empty.
- Playing on a DAP over Infinity Link: a slow connection no longer holds up the whole app while the song's title and cover go to the DAP.
- Several rare timing problems that could stop playback or the app are fixed.
