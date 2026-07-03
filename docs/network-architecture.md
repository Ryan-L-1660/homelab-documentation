# Network Architechture
Network Subnet: 192.168.20.0/24  
Router DHCPv4 Range: 192.168.20.1-200/24  

```mermaid
flowchart LR
    %% Uplink / Core
    Router["🛜 Router<br/>IP: 192.168.20.1"] -->|"Port 1.0.22"| ATSwitch["⇆ Allied Telesis x230-28GT<br/>IP: 192.168.20.205"]

    %% Endpoints & Infrastructure
    ATSwitch -->|"Port 1.0.1"| RoomLink["🏠 Link to Other Room<br/>(DHCP)"]
    ATSwitch -->|"Port 1.0.3"| MainPC["🖥️ Main-PC<br/>(Windows/Gaming)<br/>IP: 192.168.20.254"]
    ATSwitch -->|"Port 1.0.5"| TestDesk["🔧 Desk Test Bench<br/>(Static or DHCP)"]
    
    %% Servers & Services
    ATSwitch -->|"Port 1.0.7"| DebGUI["🐧 Debian 13 GUI Server<br/>IP: 192.168.20.213"]
    ATSwitch -->|"Port 1.0.9"| Technitium["🛡️ Debian Technitium<br/>IP: 192.168.20.212"]
    ATSwitch -->|"Port 1.0.11"| TrueNAS["💾 TrueNAS Scale<br/>IP: 192.168.20.250"]
    ATSwitch -->|"Port 1.0.13"| PiHole["🕳️ Debian Pi-hole<br/>IP: 192.168.20.211"]
    
    %% Bridge / Downlink Switches
    ATSwitch -->|"Port 1.0.24"| Brocade["🔌 Brocade 6910<br/>(Port 8)<br/>Mgmt IP: 192.168.20.204"]

    %% Styling for GitHub Dark/Light Mode Compatibility
    classDef switch fill:#2d3748,stroke:#718096,stroke-width:2px,color:#ffffff;
    classDef server fill:#1a365d,stroke:#2b6cb0,stroke-width:1px,color:#ffffff;
    classDef client fill:#22543d,stroke:#2f855a,stroke-width:1px,color:#ffffff;
    classDef uplink fill:#4a5568,stroke:#a0aec0,stroke-width:1px,color:#ffffff;

    class ATSwitch,Brocade switch;
    class DebGUI,Technitium,TrueNAS,PiHole server;
    class MainPC,TestDesk client;
    class Router,RoomLink uplink;


