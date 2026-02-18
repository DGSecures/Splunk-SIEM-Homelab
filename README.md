# Splunk-SIEM-Homelab
A centralized Windows log collection homelab using Splunk Enterprise and Splunk Universal Forwarders on Windows client virtual machines. This repository documents the virtualized lab setup, index configuration, and sample searches to validate log ingestion and security monitoring. 

## Overview
- Goal: Configure a Splunk Enterprise server on Ubuntu and ingest Windows Event Logs from endpoints using Splunk Universal Forwarders.
- Purpose: Cenetralized log detection is foundational for incident response, threat detection, and SOC workflows.

## Architecture
- Splunk Server: Ubuntu Server VM
- Endpoints: 2x Windows Client VMs
- Admin: IT VM used to acces Splunk Web

## High Level Diagram
<img width="598" height="519" alt="Screenshot 2026-02-11 at 9 35 37 PM" src="https://github.com/user-attachments/assets/8a70aaab-7b74-41c7-ad27-3093bc4948b7" />

## Build Steps (High Level)
### Splunk Server Setup (Ubuntu)

### Splunk Web Access Setup
After installing Splunk Server on the Ubuntu VM, we enabled web access to Splunk Web management which runs on TCP port 8000.
This web interface is where we configure our Splunk indexes and apps. 

Within the web management interface, we install Splunk Add-on for Microsoft Windows.
The purpose of this add-on is to provide input for Windows data sources and parsing. 

### Windows Forwarder Setup (Clients)
First thing that was done on the 2 client machines was to download and install the Splunk Universal Forwarder on each one.
The purpose of the Splunk Universal Forwarder is to collect the local Windows logs and send them to the centralized Splunk Server.

An inputs.conf file was created that would to ingest Windows logs from Event Viewer which include Security, System, and Application logs.
Within the inputs.conf file, we also define the Splunk index to route the logs properly for searching.

After the setup is complete, we restart the SplunkForwarder service to ensure the forwarder was connected to the Splunk server and events are being transmitted.

## Example Searches

## Issues Encountered & Fixes
