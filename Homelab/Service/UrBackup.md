# UrBackup

## Overview

UrBackup is used as the primary backup solution for personal data stored on my workstation.

The objective is to ensure that important files can be recovered in the event of accidental deletion, hardware failure, or system reinstallation while keeping storage requirements under control.

---

## Objectives

The backup strategy was designed around three main goals:

* Protect important personal files
* Minimize storage consumption
* Simplify data recovery

Rather than backing up the entire workstation, only valuable and non-replaceable data is protected.

---

## Backup Scope

The backup system focuses on personal files and documents, including:

* Administrative documents
* Personal projects
* Configuration files
* Other important user data

Data that can easily be recovered or re-downloaded is intentionally excluded.

Examples include:

* Video games
* Software installers
* Temporary files
* Reproducible data

This approach significantly reduces storage usage while maintaining protection for critical information.

---

## Storage Architecture

Backups are stored on a dedicated SSD connected to the Raspberry Pi.

The storage device is automatically mounted during system startup, allowing backups to run without manual intervention.

This configuration provides:

* Dedicated backup storage
* Reduced dependency on the workstation
* Centralized backup management

---

## Backup Strategy

UrBackup performs daily file-level backups of the workstation.

The schedule was chosen to provide a balance between:

* Data protection
* Storage efficiency
* Resource consumption

The backup process runs automatically and requires minimal maintenance.

---

## Recovery Testing

Backup verification is considered as important as backup creation.

Recovery procedures were successfully tested by restoring backed-up files, confirming that the backup system functions as intended.

This validation ensures that protected data can effectively be recovered when needed.

---

## Why UrBackup?

Several backup approaches were considered before selecting UrBackup.

The primary selection criteria were:

* Storage efficiency
* Ease of deployment
* Automated operation
* Low maintenance requirements

Given the limited storage capacity available within the homelab, storage optimization was a major factor in the decision-making process.

---

## Lessons Learned

Deploying a backup solution highlighted the importance of distinguishing between valuable data and data that can easily be recreated.

Key takeaways include:

* Not all data requires backup protection
* Storage planning is an important part of backup design
* Automated backups reduce the risk of human error
* Recovery testing is essential to validate a backup strategy
* A successful backup is only useful if restoration is possible
