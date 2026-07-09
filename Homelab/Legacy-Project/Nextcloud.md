# Nextcloud

## Overview

Nextcloud was one of the first self-hosted services deployed within the homelab.

The project was initially created to provide a personal cloud platform while also serving as an introduction to containerized applications and self-hosted infrastructure.

Although the service is no longer in production, it played an important role in the early development of the homelab.

---

## Objectives

The deployment was motivated by two primary goals:

* Create a personal cloud storage solution
* Gain practical experience with Docker and self-hosted services

At the time, the project represented an opportunity to explore alternatives to commercial cloud platforms while learning the fundamentals of containerized deployments.

---

## Features Used

The platform was primarily used for:

* File synchronization
* Photo sharing

These features provided a convenient way to access personal files across multiple devices while maintaining control over the hosted data.

---

## Architecture

Nextcloud was deployed as a Docker container on the Raspberry Pi.

Data was stored directly on the Raspberry Pi's SD card, which simplified the initial setup and allowed the project to be deployed quickly for experimentation purposes.

The deployment served as one of the first practical introductions to:

* Docker containers
* Persistent storage
* Web application hosting
* Service administration

---

## Operational Experience

The service was actively used for several weeks and successfully fulfilled its intended purpose.

The project provided valuable hands-on experience with self-hosting concepts and demonstrated how containerized services could be deployed and managed on low-power hardware.

For an early homelab project, the deployment proved to be both educational and functional.

---

## Why the Project Was Retired

The service was retired following the acquisition of a dedicated Synology NAS.

The NAS already included integrated file management, synchronization, and sharing capabilities through Synology Drive.

Because these features were available as part of the storage platform itself, maintaining a separate Nextcloud deployment no longer provided significant benefits.

As a result, the infrastructure was simplified by consolidating storage-related services onto the NAS.

---

## Replacement

The functionality previously provided by Nextcloud is now handled through:

* Synology Drive
* Native NAS file-sharing capabilities

This transition reduced management overhead while providing a more integrated storage experience.

---

## Lessons Learned

This project was one of the earliest self-hosted services deployed within the homelab and provided valuable practical experience.

Key takeaways include:

* Understanding the fundamentals of Docker and containerized applications
* Learning how persistent storage is managed within containers
* Gaining experience with self-hosted web services
* Understanding the trade-offs between self-hosted platforms and dedicated appliances
* Recognizing when a specialized solution can simplify infrastructure management

---

## Impact

Although the deployment was eventually retired, it served as an important milestone in the development of the homelab.

The project provided foundational knowledge that would later be applied to many other self-hosted services running within the environment.
