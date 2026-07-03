# Network Architechture
```mermaid
graph TD
    Internet((Internet)) --> OPNsense[OPNsense Router-on-a-Stick]
    OPNsense --> Switch[Managed Switch]
    
    subgraph VLAN 10 - Management
        Switch --> MainPC[Arch Linux Workstation]
        Switch --> PiHole[Rocky Linux - Pi-hole DNS]
    end
    
    subgraph VLAN 20 - Lab Cluster
        Switch --> Node1[Hardware Node 1]
        Switch --> Node2[Hardware Node 2]
    end


