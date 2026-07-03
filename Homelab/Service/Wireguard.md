# WireGuard VPN

## Overview

WireGuard provides secure remote access to the homelab environment.

It allows access to self-hosted services and administrative interfaces from external networks while avoiding direct exposure of those services to the Internet.

WireGuard is the only service exposed through port forwarding on the ISP router, making it the single entry point into the homelab infrastructure.

---

## Objectives

The VPN was deployed to:

* Securely administer the Raspberry Pi remotely
* Access internal web interfaces
* Access self-hosted services while away from home
* Reduce the attack surface by avoiding direct Internet exposure
* Provide a consistent access method regardless of location

---

## Design Choices

### Initial OpenVPN Deployment

The first VPN implementation used OpenVPN.

At the time, OpenVPN was selected because it was the most widely known VPN solution and represented a familiar starting point for remote access experimentation.

### Migration to WireGuard

The infrastructure was later migrated to WireGuard.

The decision was primarily motivated by:

* Simpler configuration
* Reduced maintenance overhead
* Better performance
* Improved experience on mobile devices

WireGuard ultimately provided a cleaner and more lightweight solution for the homelab environment.

---

## Remote Access Architecture

Remote access is achieved through a combination of:

* WireGuard VPN
* Dynamic DNS (No-IP)
* Port forwarding on the ISP router

The Dynamic DNS service allows the VPN endpoint to remain accessible even when the public IP address changes.

Only the WireGuard service is exposed externally.

All other services remain accessible exclusively through:

* The local network
* Authenticated VPN clients

---

## Authentication

WireGuard clients authenticate using cryptographic key pairs.

This approach eliminates the need for password-based authentication and provides a simple and secure access mechanism.

---

## Usage

The VPN is used as the primary method for accessing internal resources remotely, including:

* Raspberry Pi administration
* Self-hosted applications
* Home Assistant
* Backup services
* Internal web interfaces

The VPN effectively extends the home network to trusted remote devices.

---

## Security Considerations

Several principles guided the deployment:

* Minimize publicly exposed services
* Restrict remote access to authenticated devices
* Maintain a single controlled entry point
* Separate external access from application exposure

This design significantly reduces the number of services reachable from the Internet.

---

## Lessons Learned

Deploying a VPN highlighted the importance of secure remote administration in a self-hosted environment.

Key takeaways include:

* Remote access should be secured before exposing services externally
* Dynamic DNS simplifies access to residential Internet connections
* Simplicity often improves maintainability
* WireGuard provides an excellent balance between security, performance, and usability for personal infrastructure
