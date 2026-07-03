# Network Architechture
```mermaid
flowchart LR
    %% Uplink / Core
    Router["🌐 Router"] -->|"Port 1.0.22"| ATSwitch["🔌 Allied Telesis Switch<br/>x230-28gt"]

    %% Endpoints & Infrastructure
    ATSwitch -->|"Port 1.0.1"| RoomLink["🏠 Link to Other Room"]
    ATSwitch -->|"Port 1.0.3"| MainPC["🖥️ Main-PC<br/>(Windows/Gaming)"]
    ATSwitch -->|"Port 1.0.5"| TestDesk["🔧 Desk Test Bench<br/>(New Equipment Testing)"]
    
    %% Servers & Services
    ATSwitch -->|"Port 1.0.7"| DebGUI["🐧 Debian 13 GUI Server<br/>(Config Testing)"]
    ATSwitch -->|"Port 1.0.9"| Technitium["🛡️ Debian Technitium Machine"]
    ATSwitch -->|"Port 1.0.11"| TrueNAS["💾 TrueNAS Scale"]
    ATSwitch -->|"Port 1.0.13"| PiHole["🕳️ Debian Pi-hole Machine"]
    
    %% Bridge / Downlink Switches
    ATSwitch -->|"Port 1.0.24"| Brocade["🔌 Brocade 6910<br/>(Port 8)"]

    %% Styling for GitHub Dark/Light Mode Compatibility
    classDef switch fill:#2d3748,stroke:#718096,stroke-width:2px,color:#ffffff;
    classDef server fill:#1a365d,stroke:#2b6cb0,stroke-width:1px,color:#ffffff;
    classDef client fill:#22543d,stroke:#2f855a,stroke-width:1px,color:#ffffff;
    classDef uplink fill:#4a5568,stroke:#a0aec0,stroke-width:1px,color:#ffffff;

    class ATSwitch,Brocade switch;
    class DebGUI,Technitium,TrueNAS,PiHole server;
    class MainPC,TestDesk client;
    class Router,RoomLink uplink;


