# FileBrowser

## Overview

FileBrowser was deployed as a lightweight file-sharing platform designed to simplify file transfers between friends.

The service provided a simple web interface for uploading and downloading files without relying on third-party services such as WeTransfer or Discord Nitro.

Unlike personal cloud solutions, the objective was not long-term storage but rather temporary and convenient file exchange.

---

## Objectives

The project was created to address several requirements:

* Simplify file sharing between friends
* Avoid file size limitations imposed by some online services
* Maintain control over shared content
* Gain additional experience with self-hosted web applications

The service offered a straightforward solution focused exclusively on file transfers.

---

## Why FileBrowser?

At the time, Nextcloud had already been deployed within the homelab.

However, granting friends access to a personal cloud environment was not considered appropriate for the intended use case.

FileBrowser provided a cleaner separation between:

* Personal storage
* Shared content

This made it possible to exchange files without exposing personal data or creating additional user management requirements.

---

## Architecture

FileBrowser was deployed as a Docker container on the Raspberry Pi.

Shared files were stored on the Raspberry Pi's SD card and accessed through a web-based interface.

Access to the service was restricted through the existing VPN infrastructure.

As a result, only authenticated VPN users could access the platform.

This approach aligned with the overall security model of the homelab by avoiding direct Internet exposure.

---

## Operational Experience

The service was primarily used during the development of a separate Go-based web application project.

Friends who contributed to the project used FileBrowser to exchange files and project-related resources.

The platform proved effective for this purpose due to its simplicity and minimal administrative requirements.

---

## Why the Project Was Retired

The service was used for approximately two to three weeks before becoming unnecessary.

Its primary purpose was tied to collaboration around the Go web application project.

When development of that project stopped, the need for dedicated file-sharing capabilities disappeared as well.

As a result, the service was retired rather than maintained without an active use case.

---

## Security Considerations

FileBrowser was intentionally restricted to VPN users.

This decision provided several benefits:

* No direct Internet exposure
* Access limited to trusted users
* Reduced attack surface
* Consistency with the security model used across the homelab

The service remained one of the few applications designed specifically for VPN-based collaboration.

---

## Lessons Learned

Although relatively short-lived, the project provided useful practical experience.

Key takeaways include:

* Different use cases may require different storage solutions
* Lightweight tools can be more appropriate than feature-rich platforms depending on requirements
* VPN-based access can simplify the security model of collaborative services
* Self-hosted solutions can effectively replace certain third-party file-sharing platforms
* Not every project needs to remain active to provide learning value

---

## Impact

While the deployment was temporary, it demonstrated how a simple self-hosted application could solve a specific problem efficiently.

The project also reinforced the importance of selecting tools based on actual requirements rather than deploying a single solution for every use case.
