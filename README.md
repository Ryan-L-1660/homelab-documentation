# Homelab Documenation Summary

## Overview
This is my documentation for my homelab, self hosting multiple services.

## Basic Lab Hardware Overview
### Networking
- Allied Telesis x230-28GT
- Brocade 6910

### Computers
- Debian 1 (Technitium): HP Elite Desk 800
- Debian 2 (Pi-hole): HP Prodesk 
- Debian 3 (Test GUI Server): HP Elite Desk 600
- NAS: HP Elite Desk 800

## Network Architechture Framework
Internet   
  ↓        
Allied Telesis x230-28GT    
``` port1.0.1 - Uplink 
	port1.0.2 - Link to Main PC
	port1.0.3 - Link to TrueNAS SCALE 
	port1.0.4 - Link to Debian Server 1 (Technitium)
	port1.0.5 - Link to Debian Server 2 (Pi-hole)
	port1.0.6 - Link to Debian Server 3 (Testing/Experiments)
```
