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
      - /path/to/your/music:/music:ro
    # devices:                    # only for a USB DAC plugged into this machine: remove the two #
    #   - /dev/snd:/dev/snd
```

Music in more than one place: mount each folder inside `/music`. Everything under `/music` is one library.

```yaml
    volumes:
      - ./data:/data
      - /mnt/disk1/music:/music/disk1:ro
      - /mnt/disk2/flac:/music/disk2:ro
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
      - /mnt/tank/music:/music:ro
```

   More than one music dataset: one line each, inside `/music` (e.g. `/mnt/tank/flac:/music/flac:ro`).

3. Open **`http://<your TrueNAS address>:8930`** in a browser. To pair it, press **Show a code**, then in TrueNAS open
   Apps › infinity-core › Workloads › the log icon beside the container: the six-digit code is at the bottom. Type it
   on the page. Each browser pairs once.
4. Infinity Core for Mac or Windows can use it too: System › Shell, `sudo docker ps` shows the container's name, then
   `sudo docker exec <name> infinity-core --pair-code` gives the code for it.

Images: `ghcr.io/tekchansin/infinity-core` for amd64 (Intel and AMD computers). arm64 (Raspberry Pi, Home Assistant
Green and Yellow) follows in a later version. This repository holds the add-on's
description only; Infinity Core's own code is not open source.
