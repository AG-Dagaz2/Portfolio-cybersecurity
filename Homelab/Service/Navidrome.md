# Navidrome

## Overview

Navidrome is deployed as a self-hosted music streaming platform within the homelab.

The service provides access to a personal music library from multiple devices while maintaining full control over the hosted content.

Unlike commercial streaming services, Navidrome allows music to be managed and accessed without recurring subscription costs.

---

## Objectives

The deployment of Navidrome was motivated by two primary goals:

* Explore self-hosted media solutions
* Access a personal music collection from anywhere

The project also provided an opportunity to evaluate alternatives to commercial music streaming platforms.

---

## Architecture

Navidrome is hosted on the Raspberry Pi and stores its music library locally.

The service is accessible through:

* The local network
* The WireGuard VPN infrastructure

This approach allows secure remote access without exposing the application directly to the Internet.

---

## Music Library

The platform currently hosts a personal collection of approximately one hundred tracks.

While relatively small, the collection is actively maintained and used on a daily basis.

The objective is not to compete with commercial streaming catalogs but rather to provide convenient access to personally owned music.

---

## Client Applications

Navidrome is accessed through multiple interfaces depending on the device being used.

### Desktop Usage

The web interface is primarily used when listening from a computer.

### Mobile Usage

An Android client is used for mobile access, allowing the music library to remain available while away from home through the VPN connection.

The compatibility with mobile applications was one of the most appealing aspects of the platform.

---

## Operational Experience

The deployment process was straightforward and required very little maintenance after the initial setup.

The service has proven to be reliable enough for daily use and integrates naturally into the existing homelab environment.

Unlike some self-hosted applications, no significant operational issues were encountered during deployment or day-to-day operation.

---

## Why Navidrome?

Navidrome was selected as the initial solution for self-hosted music streaming.

The platform immediately met all requirements and therefore no migration to alternative solutions was necessary.

The most compelling aspects of the project were:

* Simplicity
* Lightweight resource usage
* Mobile compatibility
* Ease of administration

These characteristics made it particularly suitable for deployment on a Raspberry Pi.

---

## Security Considerations

The service is not exposed directly to the Internet.

Access is restricted to:

* Local network users
* Authenticated WireGuard VPN clients

This design minimizes external exposure while maintaining convenient remote access.

---

## Lessons Learned

Deploying Navidrome provided practical experience with self-hosted media services and remote content access.

Key takeaways include:

* Self-hosted services can effectively replace certain subscription-based platforms
* Lightweight applications are well suited for Raspberry Pi environments
* Mobile compatibility is essential for media-oriented services
* Not all self-hosted projects require complex architectures to provide value
* Simplicity often contributes significantly to long-term reliability

---

## Impact

Navidrome has become one of the most frequently used services within the homelab.

Its daily use demonstrates the practical value of self-hosting beyond experimentation and technical learning.
