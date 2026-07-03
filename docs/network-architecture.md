# Network Architecture
* **Network Subnet:** `192.168.20.0/24`  
* **Router DHCPv4 Range:** `192.168.20.2-200/24`  

```mermaid
flowchart LR
    %% Left Side Control Panel (Fills the top-left & bottom-left void completely)
    subgraph LeftPanel ["📝 Info & Diagram Key"]
        direction TB
        Meta["⚙️ Subnet: 192.168.20.0/24<br/>🚌 DHCP: 192.168.20.2 - .200"]:::meta
        K1["🌐 Uplink / Infrastructure"]:::uplink
        K2["🔌 Network Switch"]:::switch
        K3["💾 Server / Service"]:::server
        K4["🖥️ Client / Test Bench"]:::client
    end

    %% Core Infrastructure
    Router["🌐 Router<br/>IP: 192.168.20.1"] -->|"Port 1.0.22"| ATSwitch["🔌 Allied Telesis Switch<br/>x230-28GT<br/>IP: 192.168.20.205"]

    %% Endpoints & Infrastructure
    ATSwitch -->|"Port 1.0.1"| RoomLink["🏠 Link to Other Room<br/>(DHCP)"]
    ATSwitch -->|"Port 1.0.3"| MainPC["🖥️ Main-PC<br/>(Windows/Gaming)<br/>IP: 192.168.20.254"]
    ATSwitch -->|"Port 1.0.5"| TestDesk["🔧 Desk Test Bench<br/>(Static or DHCP)"]
    
    %% Servers & Services
    ATSwitch -->|"Port 1.0.7"| DebGUI["🔮 Debian 13 GUI Server<br/>IP: 192.168.20.213"]
    ATSwitch -->|"Port 1.0.9"| Technitium["🛡️ Debian Technitium<br/>IP: 192.168.20.212"]
    ATSwitch -->|"Port 1.0.11"| TrueNAS["💾 TrueNAS Scale<br/>IP: 192.168.20.250"]
    ATSwitch -->|"Port 1.0.13"| PiHole["🕳️ Debian Pi-hole<br/>IP: 192.168.20.211"]
    
    %% Bridge / Downlink Switches
    ATSwitch -->|"Port 1.0.24"| Brocade["🔌 Brocade 6910<br/>(Port 8)<br/>Mgmt IP: 192.168.20.X"]

    %% Invisible spacer pushing the canvas boundary down on the right
    %% This shields the Brocade text from GitHub's floating zoom UI
    Brocade ~~~ Spacer["<br/><br/>"]

    %% Style Definitions & Themes
    style Spacer fill:none,stroke:none,color:#00000000
    style LeftPanel fill:#1a202c,stroke:#2d3748,color:#edf2f7
    
    classDef meta fill:#2d3748,stroke:#4a5568,stroke-width:1px,color:#cbd5e0;
    classDef switch fill:#2d3748,stroke:#718096,stroke-width:2px,color:#ffffff;
    classDef server fill:#1a365d,stroke:#2b6cb0,stroke-width:1px,color:#ffffff;
    classDef client fill:#22543d,stroke:#2f855a,stroke-width:1px,color:#ffffff;
    classDef uplink fill:#4a5568,stroke:#a0aec0,stroke-width:1px,color:#ffffff;

    class ATSwitch,Brocade switch;
    class DebGUI,Technitium,TrueNAS,PiHole server;
    class MainPC,TestDesk client;
    class Router,RoomLink uplink;

