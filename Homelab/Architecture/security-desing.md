# Security Design

## Objectives

The primary objective of the homelab security design is to reduce the attack surface of the network while maintaining ease of use for daily operations.

Security measures were implemented both at the network level and at the wireless infrastructure level.

---

## Router Hardening

### Default Credential Replacement

The default administrative password of the ISP router was replaced with a unique password exceeding 80 characters.

This measure helps prevent unauthorized access resulting from weak or default credentials.

### ISP Wi-Fi Disabled

The wireless functionality of the ISP router was disabled.

All wireless communications are handled exclusively by the mesh network infrastructure, providing centralized management and reducing unnecessary attack surfaces.

---

## Wireless Network Segmentation

The mesh network was configured with three dedicated SSIDs:

### Private Network

Used by trusted personal devices such as laptops, desktops, and smartphones.

### IoT Network

Dedicated to connected devices and home automation equipment.

Separating IoT devices from daily-use devices reduces the impact of potential vulnerabilities affecting smart devices.

### Guest Network

Reserved for visitors and temporary devices.

This prevents guest devices from accessing internal resources and services hosted within the homelab.

---

## Wireless Security

### Strong Authentication

Each wireless network is protected using unique passwords generated with more than 80 characters.

### WPA2/WPA3 Encryption

Only WPA2 and WPA3 security protocols are enabled.

Legacy and insecure wireless authentication methods are disabled to improve network protection.

### WPS Disabled

Wi-Fi Protected Setup (WPS) was disabled.

WPS has historically been affected by multiple security weaknesses and provides an unnecessary attack vector in a manually managed environment.

---

## Security Benefits

The implemented design provides several advantages:

* Reduced exposure to default credential attacks
* Segregation of device categories through dedicated SSIDs
* Improved protection of internal services
* Strong wireless authentication mechanisms
* Elimination of unnecessary wireless attack vectors
* Better control over devices connected to the network
