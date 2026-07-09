# Homelab

A self-hosted infrastructure built around a Raspberry Pi 5 and designed to explore system administration, networking, security, automation, backup strategies, and self-hosting technologies.

The homelab serves both as a learning environment and as a production environment for several services used on a daily basis.

---

## Table of Contents

* [Architecture](#architecture)
* [Active Services](#active-services)
* [Legacy Projects](#legacy-projects)
* [Technologies Used](#technologies-used)

---

## Architecture

### Documentation

* [Network Topology](architecture/network-topology.md)
* [Security Design](architecture/security-design.md)
* [Design Philosophy](architecture/design-philosophy.md)

---

## Active Services

| Service                                     | Purpose                              |
| ------------------------------------------- | ------------------------------------ |
| [WireGuard](services/wireguard.md)          | Secure remote access                 |
| [Pi-hole](services/pihole.md)               | DNS filtering and network visibility |
| [UrBackup](services/urbackup.md)            | Automated file backups               |
| [Home Assistant](services/homeassistant.md) | Home automation platform             |
| [Navidrome](services/navidrome.md)          | Self-hosted music streaming          |
| [Minecraft Server](services/minecraft.md)   | Multiplayer game hosting             |

---

## Legacy Projects

These projects are no longer part of the current infrastructure but represent important milestones in the evolution of the homelab.

| Project                                                         | Description                       |
| --------------------------------------------------------------- | --------------------------------- |
| [Nextcloud](legacy-projects/nextcloud.md)                       | Personal cloud platform           |
| [FileBrowser](legacy-projects/filebrowser.md)                   | Lightweight file-sharing solution |
| [OpenVPN to WireGuard](legacy-projects/openvpn-to-wireguard.md) | VPN infrastructure migration      |

---

## Technologies Used

### Infrastructure

* Raspberry Pi 5
* Linux
* Docker
* Docker Compose
* Portainer

### Networking

* WireGuard
* Pi-hole
* DDNS (No-IP)
* TP-Link Mesh Network

### Services

* Home Assistant
* Navidrome
* UrBackup
* Minecraft Server

### Security

* VPN-only remote access
* WPA2/WPA3 wireless security
* Network separation through dedicated SSIDs
* DNS filtering

---

## Repository Structure

```text
homelab/
│
├── architecture/
├── services/
├── legacy-projects/
└── images/
```

---

## Future Improvements

Potential future developments include:

* VLAN-based network segmentation
* Additional home automation integrations
* Expanded monitoring capabilities
* Additional self-hosted services
* Enhanced backup strategy
