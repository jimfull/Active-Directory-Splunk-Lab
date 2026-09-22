# Active Directory & Splunk Home Lab

A hands-on home lab built to simulate a small enterprise network, combining Active Directory administration with a Splunk-based detection pipeline and basic attack simulation.

## Overview

This lab was built entirely in VirtualBox and includes:

- A **Windows Server 2022** domain controller running Active Directory Domain Services
- A **Windows 10** client machine joined to the domain
- An **Ubuntu Server** running **Splunk Enterprise** as a centralized log collection and analysis platform
- A **Kali Linux** attack box used to simulate real-world threats

## Architecture

![Network Diagram](link-to-your-diagram-image-if-you-add-one)

- Network: `192.168.10.0/24`
- Splunk Server: `192.168.10.10`
- Active Directory (ADDC01): `192.168.10.7`
- Target Client (target-pc): `192.168.10.5`
- Kali Attacker: `192.168.10.100`

## What I Built

**Active Directory**
- Promoted a Windows Server 2022 instance to a domain controller (`vbox.local`)
- Created organizational units (IT, HR) and domain user accounts
- Joined a Windows 10 client to the domain

**Splunk & Log Collection**
- Installed Splunk Enterprise on Ubuntu Server
- Deployed the Splunk Universal Forwarder and Sysmon on the domain-joined client and AD server
- Configured `inputs.conf` and `outputs.conf` to forward Application, Security, System, and Sysmon logs into a custom `endpoint` index
- Verified end-to-end log ingestion with live search results

**Attack Simulation & Detection**
- Used Kali Linux with Crowbar to run an RDP brute-force attack against a domain account
- Verified failed logon attempts (Event ID 4625) appearing in Splunk
- Installed Atomic Red Team and executed MITRE ATT&CK-mapped test techniques (e.g., local account creation, PowerShell execution)
- Compared visibility gaps: some techniques went undetected without proper alerting configured, demonstrating the value of detection engineering

## Skills Demonstrated

- Active Directory installation, domain promotion, and user/OU management
- Static IP and DNS configuration (netplan, Windows network settings, AD DNS forwarders)
- SIEM deployment and log pipeline troubleshooting (Splunk, Universal Forwarder, Sysmon)
- Basic offensive security tooling (Crowbar, Atomic Red Team) mapped to MITRE ATT&CK
- Real-world troubleshooting: corrupted install media, Splunk authentication issues, Kerberos/NLA authentication failures, DNS resolution problems

## Full Documentation

The complete step-by-step write-up, including screenshots and a detailed troubleshooting log for every issue encountered, is available here:
[Active_Directory_Splunk_LAB.pdf](./Active_Directory_Splunk_LAB.pdf)

## Author

Jim Fullah — Cybersecurity student at GMU
