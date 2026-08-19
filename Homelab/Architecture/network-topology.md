# Network Topology

## Overview

The homelab is hosted on a Raspberry Pi 5 with 8 GB of RAM and is connected to the home network through a TP-Link mesh Wi-Fi infrastructure.

The Raspberry Pi hosts the majority of the homelab services, while the main PC is primarily used as an administration and management workstation.

The network is designed to provide local access to self-hosted services while allowing secure remote access through WireGuard VPN.

---

## Network Infrastructure

### ISP Router

The ISP router remains the primary gateway to the Internet.

It is responsible for:

- Internet connectivity
- Routing
- DHCP
- External network access
- Port forwarding

The ISP-provided Wi-Fi has been disabled to centralize wireless connectivity through the TP-Link mesh infrastructure.

Only the WireGuard VPN service requires a port forwarding rule on the ISP router.

No other homelab service is directly exposed to the Internet.

---

### TP-Link Mesh Network

The TP-Link mesh system operates in **Access Point mode**.

Its primary role is to provide wireless coverage throughout the house while keeping the ISP router as the main network gateway.

Three separate wireless networks are configured:

| SSID | Purpose |
|------|---------|
| Private Network | Main personal devices |
| IoT Network | Smart home and connected devices |
| Guest Network | Guest devices |

This separation provides a basic logical distinction between different categories of devices.

Full VLAN-based network segmentation is considered a future improvement.

---

## Main Workstation

The main PC is connected to the network and primarily acts as an administration workstation.

It is used to:

- Connect to the Raspberry Pi through SSH
- Access web interfaces hosted by the homelab
- Manage services
- Perform system administration
- Access the homelab remotely through WireGuard when outside the local network

The PC does not host the main homelab services.

---

## Raspberry Pi 5

The Raspberry Pi 5 with 8 GB of RAM is the central computing platform of the homelab.

It hosts the majority of the infrastructure services, including:

- Pi-hole
- WireGuard
- UrBackup
- Home Assistant
- Navidrome
- Minecraft Server

Depending on the service, applications are deployed using a combination of:

- Docker Compose
- Portainer
- Native Linux installations

The Raspberry Pi is connected to the network through Ethernet.

---

## Service Access

The services hosted on the Raspberry Pi follow a common access model.

### Local Network

When connected to the home network, authorized devices can access the services directly through the LAN.

This includes web-based administration interfaces and user-facing applications.

Administrative access to the Raspberry Pi is also available through SSH from the local network.

### Remote Access

When outside the home network, access is provided through the WireGuard VPN.

The VPN creates a secure path into the internal network, allowing authorized remote devices to access services as if they were connected locally.

This avoids exposing each individual service directly to the Internet.

---

## Remote Access

WireGuard is used as the primary remote access mechanism.

The remote access path is centralized through the ISP router and the WireGuard endpoint hosted on the Raspberry Pi.

Only WireGuard requires an inbound port forwarding rule on the ISP router.

Once connected to the VPN, authorized clients can access internal services and resources through the LAN.

A DDNS service is used to provide a stable hostname for remote VPN connections despite changes to the public IP address.

---

## VPN Access

WireGuard is the current VPN solution used by the homelab.

It replaced OpenVPN after approximately five months of use.

The migration was mainly motivated by:

- Simpler configuration
- Easier administration
- Improved stability
- Better mobile support
- The opportunity to evaluate a modern VPN alternative

Approximately ten client devices have been configured to use the VPN.

Authentication relies on WireGuard cryptographic keys.

Only authorized clients with a valid WireGuard configuration can establish a VPN connection.

---

## DNS Architecture

Pi-hole provides network-wide DNS filtering for the home network.

Cloudflare and Quad9 are configured as upstream DNS providers.

Additional blocklists are used to filter advertising, tracking and unwanted domains.

The filtering configuration includes:

- Cloudflare
- Quad9
- StevenBlack hosts
- HaGeZi Multi
- HaGeZi Popup Ads
- HaGeZi Threat Intelligence Feeds
- HaGeZi Fake
- Other additional filtering sources

The goal is to provide relatively gentle DNS filtering while avoiding unnecessary disruption to legitimate websites and services.

Pi-hole operates primarily in the background, while its dashboard provides visibility into DNS activity and filtering statistics.

---

## Backup Architecture

UrBackup is hosted on the Raspberry Pi and is responsible for backing up the main PC.

The current backup configuration focuses on user files and documents rather than reinstallable applications or games.

Backups are performed daily.

Backup data is stored on a dedicated SSD mounted automatically on the Raspberry Pi.

The backup system is currently functional and remains part of the active homelab infrastructure.

---

## Home Automation Network

Home Assistant runs on the Raspberry Pi and provides the central platform for home automation.

Connected devices include:

- Smart plugs
- Television
- NVIDIA Shield
- NAS
- Main PC through Wake-on-LAN
- Mobile devices
- Robot vacuum

Home Assistant can be accessed through both the LAN and WireGuard VPN.

IoT devices are connected through the dedicated IoT wireless network.

The current automation setup is intentionally relatively simple because of the limited number of connected devices.

---

## Network Security Model

The network follows a security-oriented design based primarily on reducing external exposure and separating device categories.

The main principles are:

1. Disable unnecessary ISP Wi-Fi.
2. Use dedicated wireless networks for private, IoT and guest devices.
3. Use WPA2/WPA3 wireless security.
4. Disable WPS.
5. Restrict remote access through WireGuard.
6. Avoid exposing individual services directly to the Internet.
7. Use cryptographic keys for WireGuard authentication.
8. Keep administrative access available through the LAN and authorized VPN clients.

The current architecture prioritizes a small external attack surface while keeping the infrastructure accessible for administration.

---

## Current Limitations

The current network provides logical separation through dedicated wireless networks, but it does not yet implement complete VLAN-based network segmentation.

Future improvements could include:

- VLAN-based network segmentation
- Dedicated firewall policies between network segments
- More granular IoT isolation
- Dedicated management network
- Network monitoring and traffic analysis

These improvements would provide stronger isolation between trusted devices, IoT devices and guest devices.

---

## Design Principles

### Minimize Internet Exposure

Only the WireGuard VPN endpoint is exposed externally.

Individual services are not directly published to the Internet.

### Centralize Remote Access

WireGuard acts as the primary remote entry point into the homelab.

### Separate Device Categories

Private, IoT and guest devices use separate wireless networks.

### Keep Administration Accessible

Administrative interfaces remain accessible from trusted LAN devices and authorized VPN clients.

SSH access to the Raspberry Pi is also restricted to trusted network access through the LAN or VPN.

### Prefer Simplicity

The network is designed to remain understandable and maintainable rather than introducing unnecessary complexity.

---

## Summary

The current homelab network is centered around an ISP router, a TP-Link mesh system operating in Access Point mode, and a Raspberry Pi 5 connected through Ethernet.

The Raspberry Pi provides the majority of the self-hosted services, while the main PC acts primarily as an administration workstation.

Local users can access services directly through the LAN, while remote access is centralized through WireGuard.

The current architecture provides:

- Centralized remote access
- Limited Internet exposure
- Separate wireless networks for private, IoT and guest devices
- Network-wide DNS filtering
- Centralized service hosting
- Automated backups
- Home automation
- Local and remote administration

The infrastructure remains intentionally simple while providing a practical environment for experimenting with networking, Linux administration, self-hosting and security.

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/b6fdfbb0-1132-423e-b8eb-fc12ebeac42e" />
