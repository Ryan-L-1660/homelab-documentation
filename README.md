# Homelab Documenation Summary

## Overview
This is my documentation for my homelab self hosting multiple different services.

## Basic Lab Hardware Overview
### Networking
- Allied Telesis x230-28GT
- Brocade 6910

### Computers
#### Debian 1, 2, and TrueNAS Scale
- HP Elite Desk 800 G2
#### Debian 3
- HP Elite Desk 600 G2



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
