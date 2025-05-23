```mermaid
%%{init: {"theme": "forest"}}%%
sequenceDiagram
    participant Attacker
    participant Botnet
    participant Firewall
    participant WebServer

    note over Attacker,Botnet: Attacker infects multiple PCs to form Botnet

    Attacker->>Botnet: Start DDoS
    loop Flood Traffic
        Botnet->>Firewall: Send massive requests
    end

    alt Detects Attack
        Firewall-->>Botnet: Block traffic
        Firewall->>WebServer: Forward limited
    else Overwhelmed
        Firewall->>WebServer: Let all traffic through
    end

    WebServer-->>Firewall: Overloaded
