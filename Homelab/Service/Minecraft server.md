# Minecraft Server

## Overview

A self-hosted Minecraft server was deployed on the Raspberry Pi to provide a private multiplayer environment for friends.

The project was initially created to avoid recurring hosting costs while also providing hands-on experience with hosting and maintaining a multi-user service.

Although not continuously active, the server is regularly brought back online whenever a new Minecraft playthrough is started.

---

## Objectives

The deployment was motivated by several goals:

* Play with friends in a private environment
* Avoid the cost of commercial hosting providers
* Learn how to host and maintain a multiplayer service
* Experiment with the capabilities and limitations of Raspberry Pi hardware

The project combines both entertainment and technical learning objectives.

---

## Architecture

The Minecraft server is hosted on the Raspberry Pi alongside the other homelab services.

The environment has been used with both:

* Vanilla Minecraft
* Forge-based modpacks

Depending on the selected game version and modpack complexity, the hardware requirements can vary significantly.

---

## Access Model

The server was originally accessible through a dedicated port forwarding rule on the ISP router.

While functional, this approach increased the external exposure of the service.

The architecture was later modified to use the existing WireGuard VPN infrastructure.

Today, players connect through the VPN before accessing the server, eliminating the need to expose the Minecraft service directly to the Internet.

This approach aligns with the overall security model of the homelab, where external access is centralized through a single VPN entry point.

---

## Backup Strategy

World data is backed up automatically to protect against:

* World corruption
* Configuration errors
* Accidental data loss

Given the amount of time invested in multiplayer worlds, backup automation quickly became an essential component of the deployment.

The project reinforced the importance of considering recovery procedures before problems occur.

---

## Performance Challenges

The most significant challenge encountered during operation was resource management.

While Vanilla Minecraft generally operated without major issues, heavily modded Forge environments placed significantly greater demands on the Raspberry Pi.

As player counts increased and modpacks became more complex, memory limitations became apparent.

To maintain stability, swap space was increased to provide additional memory capacity during peak usage periods.

Although this mitigation improved reliability, it also highlighted the physical limitations of running demanding workloads on low-power hardware.

---

## Operational Experience

The server has hosted multiplayer sessions for approximately five to six players.

The deployment demonstrated that even relatively modest hardware can successfully host multiplayer services when properly configured and maintained.

At the same time, it provided valuable insight into capacity planning and performance tuning.

---

## Security Considerations

The current deployment follows the same security principles as the rest of the homelab:

* No direct Internet exposure
* Access restricted to VPN clients
* Centralized remote access through WireGuard

This design significantly reduces the attack surface compared to traditional public server hosting.

---

## Lessons Learned

Operating a Minecraft server provided practical experience in service hosting, performance management, and backup planning.

Key takeaways include:

* Resource requirements can increase dramatically when using large modpacks
* Backup automation is essential for protecting long-term projects
* Low-power hardware can successfully host multiplayer services when expectations are realistic
* Network exposure should be minimized whenever possible
* Capacity planning becomes increasingly important as the number of users grows

---

## Impact

Beyond its entertainment value, the Minecraft server served as a practical learning platform for infrastructure management.

It demonstrated both the strengths and limitations of self-hosted services running on constrained hardware while providing a useful service for friends and family.
