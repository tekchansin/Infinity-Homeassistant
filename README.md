# Infinity Core — Home Assistant add-on and Docker image

Infinity Core is a music library and player: your music files, Qobuz, TIDAL and internet radio in one library, played
bit-perfect on a USB DAC, on an iBasso DAP over Infinity Link, or on AirPlay, Google Cast and UPnP speakers. The same
app runs on Mac and Windows; here it runs on your Home Assistant box or any Linux server with Docker.

More: https://anantarultimate.com/infinity-core.html · Help: https://discord.gg/Z9T8VfshVs

## Home Assistant

[![Add this repository to Home Assistant](https://my.home-assistant.io/badges/supervisor_add_addon_repository.svg)](https://my.home-assistant.io/redirect/supervisor_add_addon_repository/?repository_url=https%3A%2F%2Fgithub.com%2Ftekchansin%2FInfinity-Homeassistant)

Or: Settings › Add-ons › Add-on store › ⋮ › **Repositories** → `https://github.com/tekchansin/Infinity-Homeassistant`.

| Add-on | Channel |
|---|---|
| **Infinity Core (beta)** | new versions first |
| **Infinity Core** | stable releases (from the first stable) |

Install one of them. Updates appear in Home Assistant as usual. For now it runs on Home Assistant on an Intel or AMD
computer; Raspberry Pi and Home Assistant Green / Yellow follow in a later version.

## Docker

```yaml
services:
  infinity-core:
    image: ghcr.io/tekchansin/infinity-core:beta   # :latest once a stable is out
    container_name: infinity-core
    network_mode: host          # finds DAPs, AirPlay, Cast and UPnP speakers on your network
    restart: unless-stopped
    environment:
      INFINITY_NAME: "Home server"   # how DAPs and speakers see it
      TZ: Asia/Bangkok
    volumes:
      - ./data:/data               # library, settings, updates
      - /path/to/your/music:/music:rw
    cap_add:
      - SYS_NICE                   # the playback threads run real-time: no dropouts while the server is busy
```

A USB DAC plugged into this machine (bit-perfect, native DSD): add the sound cards. A DAC plugged in later shows up too.

```yaml
    volumes:
      - ./data:/data
      - /path/to/your/music:/music:rw
      - /dev/snd:/dev/snd          # the sound cards
    device_cgroup_rules:
      - "c 116:* rwm"              # lets Infinity Core open them
```

`:rw` lets Infinity Core write to your music: Library Health (tag edits, duplicate removal) and music copied from a DAP.
With `:ro` it can only read it, and those changes are not saved.

Music in more than one place: mount each folder inside `/music`. Everything under `/music` is one library.

```yaml
    volumes:
      - ./data:/data
      - /mnt/disk1/music:/music/disk1:rw
      - /mnt/disk2/flac:/music/disk2:rw
```

Use volumes, not symbolic links: a link inside `/music` is not followed. A folder mounted somewhere else (e.g.
`/music2`) works too: add it in Settings › Storage. After changing the volumes, run `docker compose up -d`.

Open it in a browser on your network: **`http://<your server's address>:8930`** (the log says the address). The first
time, the page pairs the browser: press **Show a code**, find the six-digit code in the container's log
(`docker logs infinity-core`) and type it. Each browser pairs once.

Infinity Core for Mac or Windows can use it too: Settings › Infinity Core › pick it, and enter the code from
`docker exec infinity-core infinity-core --pair-code`. New versions install from Settings › About, in the same
container; `docker compose pull && docker compose up -d` works too.

## TrueNAS SCALE

TrueNAS SCALE 24.10 (Electric Eel) or newer runs it as a Docker app. TrueNAS CORE (FreeBSD) has no Docker.

1. Two datasets: one for Infinity Core's library and settings (e.g. `tank/apps/infinity`) and your music.
2. Apps › Discover Apps › ⋮ › **Install via YAML**, name it `infinity-core`, and paste (your own dataset paths):

```yaml
services:
  infinity-core:
    image: ghcr.io/tekchansin/infinity-core:beta
    network_mode: host
    restart: unless-stopped
    environment:
      INFINITY_NAME: "TrueNAS"
      TZ: Asia/Bangkok
    volumes:
      - /mnt/tank/apps/infinity:/data
      - /mnt/tank/music:/music:rw
    cap_add:
      - SYS_NICE                   # the playback threads run real-time: no dropouts while the server is busy
```

   More than one music dataset: one line each, inside `/music` (e.g. `/mnt/tank/flac:/music/flac:rw`).

3. Open **`http://<your TrueNAS address>:8930`** in a browser. To pair it, press **Show a code**, then in TrueNAS open
   Apps › infinity-core › Workloads › the log icon beside the container: the six-digit code is at the bottom. Type it
   on the page. Each browser pairs once.
4. Infinity Core for Mac or Windows can use it too: System › Shell, `sudo docker ps` shows the container's name, then
   `sudo docker exec <name> infinity-core --pair-code` gives the code for it.

## Synology

DSM 7.2 or newer, on a Synology with an **Intel or AMD** processor (most "+" models). Models with a Realtek or other
ARM processor cannot run it yet: the container stops with `exec format error`. Not sure which yours has? Look up
"What kind of CPU does my Synology NAS have?" on Synology's site.

1. Package Center › install **Container Manager**. It makes a shared folder called `docker`.
2. File Station › in `docker`, make a folder `infinity-core` (Infinity Core's library and settings go there). Your
   music stays where it is, e.g. the shared folder `music`.
3. Container Manager › **Project** › Create: name `infinity-core`, path `/volume1/docker/infinity-core`, source
   **Create docker-compose.yml**, and paste (your own folders; in File Station, a folder's Properties show its path):

```yaml
services:
  infinity-core:
    image: ghcr.io/tekchansin/infinity-core:beta
    container_name: infinity-core
    network_mode: host
    restart: unless-stopped
    environment:
      INFINITY_NAME: "Synology"
      TZ: Asia/Bangkok
    volumes:
      - /volume1/docker/infinity-core:/data
      - /volume1/music:/music:rw
    cap_add:
      - SYS_NICE                   # the playback threads run real-time: no dropouts while the server is busy
```

   Use a Project, not the Container wizard: the wizard puts the container on the `bridge` network, where Infinity Core
   cannot find your DAPs and speakers. `network_mode: host` is the line that matters. Leave the web portal step off.
   More than one music folder: one line each, inside `/music` (e.g. `/volume2/flac:/music/flac:rw`).

4. Open **`http://<your Synology's address>:8930`** in a browser (port 8930, not DSM's 5000). To pair it, press
   **Show a code**, then in Container Manager › Container › infinity-core › **Log**: the six-digit code is at the bottom.
   Type it on the page. Each browser pairs once.
5. Infinity Core for Mac or Windows can use it too. It needs a code from a terminal: Control Panel › Terminal & SNMP ›
   enable SSH, sign in with an administrator account, and run `sudo docker exec infinity-core infinity-core --pair-code`.
6. DSM's firewall is off unless you turned it on. If it is on (Control Panel › Security › Firewall), allow from your home
   network: TCP 8930 and 8931, TCP 8950 (UPnP / DLNA players and Chromecast fetch the music there), UDP 8960–8979
   (AirPlay speakers), and UDP 5353 and 1900 (Bonjour and SSDP — how DAPs and speakers are found).

## Good to know on a server

**Where it plays.** A NAS or a Home Assistant box has no sound of its own, so *System output* plays nothing ("no audio
output"). Open the device list and pick where the music goes: a DAP or a phone over Infinity Link, an AirPlay, Google
Cast or UPnP speaker, or Infinity Core for Mac or Windows on a computer.

**Away from home.** In Infinity Core: Settings › Mobile App › **Link Anywhere** on, and sign in to Tailscale. On your
phone, in Infinity Core for Mobile, switch on Link Anywhere with the **same** Tailscale account. Running Tailscale on the
NAS itself (e.g. Synology's Tailscale package) is not the same: the phone can open the library through it, but Infinity
Core cannot send music back to the phone. Pair the phone at home, or with the Infinity Core shown on the phone's
Link Anywhere list — not with the NAS's own 100.x address.

Images: `ghcr.io/tekchansin/infinity-core` for amd64 (Intel and AMD computers). arm64 (Raspberry Pi, Home Assistant
Green and Yellow) follows in a later version. This repository holds the add-on's
description only; Infinity Core's own code is not open source.
