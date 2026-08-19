# Pi-hole

## Overview

Pi-hole is deployed as the primary DNS filtering solution for the entire household.

The service currently supports approximately twelve devices and provides centralized DNS filtering without requiring software installation on individual clients.

Its primary purpose is to reduce advertising, limit tracking activity, and improve visibility into network behavior.

---

## Objectives

The deployment of Pi-hole was driven by several goals:

* Reduce intrusive advertisements
* Limit tracking and telemetry
* Improve privacy across household devices
* Gain visibility into DNS activity
* Centralize DNS management

The objective was not to aggressively block every possible domain but rather to implement a balanced filtering approach that minimizes user impact while still providing meaningful protection.

---

## Architecture

Pi-hole is hosted on the Raspberry Pi and acts as the primary DNS resolver for devices connected to the network.

The service uses:

* Cloudflare DNS
* Quad9 DNS

as upstream resolvers.

This configuration combines the performance benefits of Cloudflare with the security-focused reputation filtering provided by Quad9.

---

## Filtering Strategy

The filtering configuration is based on a combination of default and custom blocklists.

Additional blocklists include:

* StevenBlack Hosts
* Hagezi Multi
* Hagezi Popup Ads
* Hagezi Threat Intelligence Feeds
* Hagezi Fake Domains

The selected lists aim to provide effective protection against:

* Advertisements
* Tracking domains
* Malicious domains
* Scam-related infrastructure

while maintaining a low rate of false positives.

---

## Operational Experience

Pi-hole operates as a background service and requires very little daily maintenance.

While the primary goal is transparent operation, the dashboard provides valuable insights into network activity, including:

* Query volume
* Blocked requests
* Most active devices
* Frequently requested domains

Current statistics indicate that approximately 28% of DNS traffic is blocked through filtering policies.

The collected data also highlights usage patterns within the household, with mobile devices generating the majority of DNS requests.

---

## Challenges

A small number of websites experienced functionality issues due to blocked domains.

These cases required temporary investigation and adjustment of filtering rules.

Such situations demonstrated the importance of balancing protection and usability when designing DNS filtering policies.

---

## Why Pi-hole?

Before deploying Pi-hole, AdGuard Home was also evaluated.

Both solutions successfully fulfilled the core requirements for DNS filtering.

Pi-hole was ultimately retained due to personal preference and the extensive amount of community documentation available.

The evaluation process provided useful experience in comparing self-hosted services with similar objectives.

---

## Security Benefits

The deployment contributes to the overall security posture of the homelab by:

* Blocking known malicious domains
* Limiting communication with tracking infrastructure
* Providing visibility into DNS activity
* Centralizing filtering policies

Although DNS filtering is not a complete security solution, it provides an effective additional layer of protection.

---

## Lessons Learned

Deploying Pi-hole provided practical experience with DNS infrastructure and network-wide filtering.

Key takeaways include:

* DNS filtering can significantly reduce unwanted traffic
* Visibility into DNS activity helps identify device behavior patterns
* Effective filtering requires balancing security and usability
* Different DNS filtering solutions often provide similar capabilities but differ in deployment and management approaches
* Network-wide solutions are often easier to manage than device-by-device configurations
