# Design Philosophy

## Overview

The homelab is designed around a simple principle:

> Deploy practical services that solve real problems while maintaining a manageable and secure infrastructure.

The environment prioritizes simplicity, usability, and learning opportunities over unnecessary complexity.

---

## Security First

A core design decision is to minimize direct Internet exposure.

With the exception of the WireGuard VPN endpoint, no internal service is accessible directly from the Internet.

Remote access is centralized through a single controlled entry point.

This approach reduces the attack surface while preserving accessibility.

---

## Self-Hosting with Purpose

Services are deployed to satisfy actual requirements rather than simply increasing the number of applications hosted.

Examples include:

* Pi-hole for DNS filtering
* UrBackup for data protection
* Home Assistant for automation
* Navidrome for music streaming

Every service should provide practical value in addition to educational value.

---

## Simplicity over Complexity

Whenever possible, solutions that are easier to operate and maintain are preferred.

Examples include:

* Migration from OpenVPN to WireGuard
* Replacing Nextcloud with NAS-native capabilities
* Restricting external access through VPN instead of exposing multiple services

A simpler architecture generally leads to improved reliability and easier troubleshooting.

---

## Incremental Improvement

The homelab evolves continuously.

New services are introduced, evaluated, improved, or retired depending on their usefulness.

Examples include:

* OpenVPN replaced by WireGuard
* Nextcloud replaced by Synology Drive
* FileBrowser retired after its original use case disappeared

Infrastructure decisions are regularly reassessed rather than treated as permanent.

---

## Learning Through Practice

The homelab serves as a practical environment for developing skills in:

* Linux administration
* Networking
* Security
* Containerization
* Service deployment
* Automation

Projects are selected based on both usefulness and learning potential.

---

## Resource Awareness

The infrastructure primarily relies on a Raspberry Pi 5.

Because resources are limited, services must be selected and configured carefully.

This constraint encourages:

* Lightweight solutions
* Efficient resource usage
* Practical capacity planning

The Minecraft server project, for example, highlighted the importance of understanding hardware limitations and workload requirements.

---

## Reliability Matters

Services intended for daily use should remain stable and require minimal maintenance.

This principle influences:

* Backup strategy
* Service selection
* Remote access architecture
* Infrastructure changes

Reliability is considered just as important as functionality.

---

## Future Direction

Future developments will continue to focus on:

* Security improvements
* Infrastructure simplification
* Automation
* Monitoring
* Practical self-hosted services

The objective is not to build the largest possible homelab, but to maintain a useful, secure, and well-documented environment.
