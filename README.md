# MISP Threat Intelligence Platform Deployment

## Overview

This project demonstrates the deployment and configuration of the Malware Information Sharing Platform (MISP) on Kali Linux using Docker. MISP is an open-source threat intelligence platform used to collect, share, and analyze Indicators of Compromise (IoCs), malware intelligence, and cybersecurity events.

<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/c87f81a3-96b5-42c6-8a73-622c44b847c0" />


## Objectives

- Deploy MISP using Docker on Kali Linux
- Configure authentication and administrative settings
- Import and manage threat intelligence feeds
- Analyze threat events and IoCs
- Automate feed synchronization using Cron jobs

## Environment

| Component | Technology |
|------------|------------|
| Operating System | Kali Linux |
| Platform | MISP |
| Containerization | Docker |
| Orchestration | Docker Compose |
| Version Control | Git |
| Automation | Cron |

---

## Installation

### Update System

```bash
apt update
apt upgrade -y
```

### Install Dependencies

```bash
apt install git -y
apt install docker-ce docker-ce-cli containerd.io
apt install docker-compose
```

<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/0c2c5d62-fbca-431c-8f6f-246cb01080c3" />


### Clone MISP Repository

```bash
git clone https://github.com/MISP/misp-docker/
cd misp-docker
```
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/3d41f8f2-752e-4c17-a19a-77e71e1afd68" />


### Configure Environment

```bash
cp template.env .env
```

### Pull Docker Images

```bash
docker-compose pull
```

### Launch MISP

```bash
docker-compose up -d
```
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/00c3cec7-468a-481d-be6f-dfdfa5d7ff3e" />

### Verify Containers

```bash
docker ps
```

---

## Security Configuration

To improve security, HTTP access was disabled in the Docker configuration and HTTPS-only access was enforced for the MISP web interface.

Benefits:

- Encrypted communication
- Reduced attack surface
- Better protection of authentication credentials

---

## Authentication Management

After deployment:

1. Logged into the MISP web interface.
2. Generated a new API authentication key.
3. Verified administrative access.
4. Reviewed platform configuration settings.

The generated API key can be used for:

- Feed synchronization
- External integrations
- Automation scripts
- TAXII server connections

---

## Threat Intelligence Feed Integration

Threat intelligence feeds were imported using JSON feed definitions.

### Tasks Performed

- Imported community feed configurations
- Enabled selected feeds
- Retrieved threat intelligence data
- Stored Indicators of Compromise (IoCs)
- Verified successful synchronization

### Intelligence Collected

- Malicious IP addresses
- Domains
- URLs
- File hashes
- Threat actor information
- Malware indicators

---

## Event Analysis

After importing feeds, MISP events became available for analysis.

### Activities

- Reviewed threat events
- Examined event metadata
- Investigated Indicators of Compromise (IoCs)
- Analyzed event tags and classifications
- Explored relationships between indicators

---

## Automation

### Manual Feed Update Command

```bash
/usr/bin/curl -XPOST --insecure \
--header "Authorization:[API_KEY]" \
--header "Accept: application/json" \
--header "Content-Type: application/json" \
https://localhost/feeds/FetchFromAllFeeds
```
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/482b6198-3cef-46dc-864d-9ee4c7c2a41a" />


### Daily Automated Update

```bash
0 1 * * * /usr/bin/curl -XPOST --insecure --header "Authorization:[API_KEY]" --header "Accept: application/json" --header "Content-Type: application/json" https://localhost/feeds/FetchFromAllFeeds
```
<img width="1024" height="768" alt="image" src="https://github.com/user-attachments/assets/b5f35e61-7dd7-44fe-ab1f-001d153183e8" />


This Cron job automatically updates threat intelligence feeds every day at 1:00 AM.

---

## Skills Demonstrated

- Threat Intelligence Management
- MISP Administration
- Docker Deployment
- Linux Administration
- API Authentication
- Feed Integration
- Security Hardening
- Event Analysis
- Threat Hunting
- Cron Job Automation

---

## Outcome

Successfully deployed a fully functional MISP instance on Kali Linux, imported threat intelligence feeds, generated API authentication keys, explored threat events, and automated feed synchronization for continuous intelligence collection.

---

## Technologies Used

- Kali Linux
- MISP
- Docker
- Docker Compose
- Git
- Cron
- REST API

---

## Tags

`Threat Intelligence` `MISP` `Cybersecurity` `SOC` `Blue Team` `Threat Hunting` `Docker` `Kali Linux` `Incident Response`
