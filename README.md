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

Use it from **Infinity Core for Mac or Windows**: Settings › Infinity Core › pick it, and enter the code from
`docker exec infinity-core infinity-core --pair-code`. New versions install from the app, in the same container
(Settings › About); `docker compose pull && docker compose up -d` works too.

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

3. The pairing code: System › Shell, `sudo docker ps` shows the container's name, then
   `sudo docker exec <name> infinity-core --pair-code`.

Images: `ghcr.io/tekchansin/infinity-core` for amd64 (Intel and AMD computers). arm64 (Raspberry Pi, Home Assistant
Green and Yellow) follows in a later version. This repository holds the add-on's
description only; Infinity Core's own code is not open source.
