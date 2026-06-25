# Homelab

## Overview

This homelab is a personal self-hosted environment running on a Raspberry Pi 5 (8GB RAM). It serves as a platform for learning, experimentation, and hosting services used on a daily basis.

The objective of this project is to develop practical skills across multiple IT domains, including system administration, networking, virtualization alternatives, service deployment, automation, backup management, and self-hosting.

Unlike many laboratory environments focused on a single technology, this homelab combines several real-world services that are actively used and maintained.

---

## Infrastructure

### Hardware

* Raspberry Pi 5 (8GB RAM)
* Personal workstation used for administration
* Dedicated NAS (added later to offload storage services)

### Network

The homelab is connected through a mesh Wi-Fi infrastructure linked to the ISP router.

The wireless network is separated into multiple SSIDs:

* Private Network
* IoT Network
* Guest Network

This separation allows connected devices to be grouped according to their purpose and usage.

---

## Services Currently Deployed

### Pi-hole

Network-wide DNS filtering solution used to:

* Block advertisements
* Reduce tracking
* Improve browsing experience
* Monitor DNS activity

Alternative solutions such as AdGuard Home were also evaluated before choosing Pi-hole.

### WireGuard VPN

Secure remote access solution allowing administration of the homelab from external networks.

This service replaced a previous OpenVPN deployment after evaluating performance, simplicity, and ease of maintenance.

### Navidrome

Self-hosted music streaming platform providing access to a personal music library from multiple devices.

### UrBackup

Centralized backup solution used to protect important systems and data.

The project provided practical experience with backup strategies, retention policies, and recovery planning.

### Home Assistant

Home automation platform used to manage and monitor connected devices.

This project introduced concepts related to IoT integration, automation workflows, and service interoperability.

### Minecraft Server

Game server hosted for personal use and multiplayer sessions with friends.

The deployment involved service management, resource monitoring, and network configuration.

---

## Previous Projects

Several services were deployed, tested, and later retired as infrastructure requirements evolved.

### Nextcloud

Self-hosted cloud storage platform.

The service was discontinued after the deployment of a dedicated NAS better suited for storage workloads.

### FileBrowser

Web-based file management solution used to access files remotely.

Retired once storage management was migrated to the NAS infrastructure.

### Go Web Application

Personal web application project developed in Go and integrating AI-related features.

The project was ultimately not completed but provided valuable experience in web service deployment and application development.

### RetroPie

Retro gaming platform project.

Explored as a proof of concept but not pursued further.

---

## Skills Developed

### System Administration

* Linux administration
* Service deployment
* Service maintenance
* Backup management
* Troubleshooting

### Networking

* DNS management
* VPN deployment
* Wireless network segmentation
* Remote access configuration

### Self-Hosting

* Application deployment
* Containerized services
* Resource optimization
* Service monitoring

### Project Management

* Evaluation of alternative solutions
* Infrastructure evolution
* Migration planning
* Documentation and maintenance

---

## Lessons Learned

This homelab demonstrated the challenges involved in maintaining production-like services in a constrained environment.

Key takeaways include:

* Balancing resource consumption on limited hardware
* Maintaining service availability
* Planning migrations between solutions
* Managing backups effectively
* Designing services around real user needs rather than technical experimentation alone

---

## Future Improvements

Planned areas of exploration include:

* Advanced monitoring
* Centralized logging
* Infrastructure automation
* Reverse proxy solutions
* Identity and access management
* Additional self-hosted services
