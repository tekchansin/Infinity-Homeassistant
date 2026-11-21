# Changelog

## 14.0-beta18
Name your music folders, and set up a server in one click.

**Highlights**
- Name your music folders: Settings › Library › ✎. Two folders both called "Music" no longer look alike — the name shows in Folders and on the Sync page too.
- Infinity Core on a server (Docker, Synology, TrueNAS, Umbrel) sets up in one click: the first browser that opens it presses Start using Infinity Core — no code to find in the log. Other browsers and apps pair with a code shown in a browser that is already paired (Settings › Devices & Sharing).

**Improvements**
- Radio is just Radio now, and the stations you keep are Saved Stations.
- Umbrel: pick your music folder, set the name DAPs see and your time zone, and play on a USB DAC plugged into the Umbrel.

**Fixes**
- Sync to a DAP: after a music folder picked for sending was removed, From was empty and Send sent nothing. It sends from your music folders as they are now.
- On Umbrel, its virtual sound cards no longer fill the device list.
- The pairing page no longer hangs on Show a code when a proxy in front answers with an error page.
