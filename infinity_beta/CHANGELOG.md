# Changelog

## 14.0-beta9
Favourites shared with Qobuz and TIDAL, a clearer Discography, and cleaner sound on your computer's own DAC.

**Highlights**
- ♡ and your Qobuz / TIDAL favourites are one: a song, album or artist you ♡ in Infinity Core is saved as a favourite on the service, and what you favourite in the service's own app gets its ♡ here. Both ways, checked every 15 minutes.
- Artist pages: Discography in sections — Albums, Singles and EPs, Live, Compilations — with your library and Qobuz / TIDAL releases side by side. The versions of one release sit behind "N versions", labelled Explicit, Clean or Dolby Atmos. Cards or a list, newest or oldest first, and an artist you never opened shows in under a second.
- Cleaner sound on this computer's DAC: pause, resume, seek and skip fade over a few milliseconds instead of clicking, and a loud master that has to be converted to another sample rate no longer clips on its peaks.
- EQ and PEQ: a band plays one curve at every sample rate. A hi-res file used to get up to 3 dB more at 20 kHz than a CD-rate one; AutoEQ / OPRA headphone presets now play as their authors fitted them. With Anantar Ultimate 14.0-beta4 the DAP's own EQ on an Infinity Link stream follows the same curve.

**New**
- Docker, TrueNAS and Synology: open Infinity Core in a browser on your network at http://<your server's address>:8930. Each browser pairs once with a code from the container's log.

**Improvements**
- "Run DSP on: Infinity Core" with every stage off no longer streams what your DAP has itself: the DAP plays its own files, Qobuz and TIDAL, and Infinity Core takes over the moment you switch a stage on.
- Infinity Core for Mobile on older phones and DAPs: the cover, bars and switches that were missing are back, pages open and close smoothly, and a slow GPU gets solid bars instead of the blur.
- The phone's device list on Home Assistant: a DAC that Home Assistant's own audio holds says so, and there is no "System output" row.

**Fixes**
- A phone or player that cannot open a sample rate it offers (a Galaxy S25 at 705.6 / 768 kHz) no longer stands silent at one position: the song starts again at the next rate down.
- Home Assistant: only this box itself and paired apps reach Infinity Core's controls (a request from the network could pass as local).
