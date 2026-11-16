# Infinity Core for Home Assistant

Infinity Core — the music engine and player — running on your Home Assistant box. Open **Infinity Core** in the sidebar: your library,
Qobuz and TIDAL, Live Radio, playlists — the same app as Infinity Core for Mac and Windows, in the language you choose
(Settings › General › Language).

Pick where the music plays in the device list (the button at the bottom right) — an **Infinity Link** DAP, an
**AirPlay** speaker, a **Google Cast** speaker or TV, a **UPnP / DLNA** player, or a **USB DAC** plugged into the Home
Assistant box itself.

## A USB DAC on the box

Plug the DAC in: it shows in the device list under the box's name (not there? restart the add-on once — Settings ›
Add-ons › Infinity Core › **Restart**). Infinity Core plays to it directly — nothing else mixes or resamples on the way:
every file at its own rate, DSD as DSD when the DAC takes it (natively, or as DoP — its ⚙ settings), and the volume is
the DAC's own.

Home Assistant's own audio takes every sound card it sees. When you pick the DAC, Infinity Core switches that card off
in Home Assistant's audio, so it is free — Home Assistant then no longer plays its own sounds (announcements, text to
speech) through that DAC. This is why the add-on asks for Supervisor access (its *manager* role).

A DAP with Infinity Link on, on the same network, shows under **Infinity Link** in that list. Not there? Press **↻** to
look again; still nothing (another network, a router that hides devices): press **+** and type the DAP's address, for
example 192.168.1.20 — the DAP's Infinity Link page shows it under **This DAP**.

## Your music

Put it in Home Assistant's **media** folder, or add a network share there (Settings › System › Storage › Add network
storage, usage *Media*) — Infinity Core finds it at `/media` and reads it from where it is (nothing is copied).
Files in `/share/music` are read too.

Infinity Core changes your files in one case only: when you edit their tags (**Edit tags…** in a track's or album's ⋯ menu)
and press **Save**. Before anything is written it shows what will change, and **Settings › Library › Tag Health** keeps
your recent saves so you can undo them. This is why the add-on asks for write access to `/media` and `/share`.

## Options

- **name** — how your DAPs and speakers see this player ("Playing from Home Assistant").
- **country** — two letters (TH, JP, US …) for Live Radio's local stations.
- **language** — for station lists and online information, e.g. `th_TH`. The app's own language is chosen inside the app.

## Install

1. Settings › Add-ons › Add-on store › ⋮ › **Repositories** — add `https://github.com/tekchansin/Infinity-Homeassistant`.
2. Find **Infinity Core (beta)** in the store › **Install** (it downloads a ready image — a minute or two).
3. **Start**, turn on **Show in sidebar**, then open **Infinity Core**.

Infinity Core and Infinity Core (beta) are the two channels: install one of them. Moving between them keeps nothing by
itself — make a backup in Settings › Backups (or to Google Drive) and restore it in the other.

## Use it from Infinity Core for Mac or Windows

Infinity Core on a Mac or a PC on the same network can show this one instead of its own — your library, playlists and
services from Home Assistant, in the app's window. In the app: **Settings › Infinity Core**, pick this one, then type the
code that **Settings › Infinity Core › Show a code** gives here. Back to the app's own any time from the same page. They
talk directly on your network (port 8931), encrypted.

## Good to know

- Remote access (an iPad or a phone, at home or away): Settings › Remote access, as on the Mac and Windows app.
- Sign in to Qobuz / TIDAL in Settings › Services. The service's page opens in a new tab; when it ends on a page that
  does not say you are signed in (TIDAL's own page, or a Home Assistant error after Qobuz), copy that page's whole
  address and paste it into the box Infinity Core shows.
- Infinity Core only answers through Home Assistant's sign-in (Ingress); other devices on the network cannot open it directly.
