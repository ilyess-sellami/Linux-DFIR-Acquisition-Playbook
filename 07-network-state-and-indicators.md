# Network State & Indicators

## Why are we analyzing network activity?

Network data reveals how a compromised system **communicates with the outside world**.
It helps identify attacker infrastructure, lateral movement, and possible data exfiltration.

Unlike logs, live network state shows **active connections and listening services in real time**.

---

## Why Network Analysis is Critical

Network investigation helps uncover:

- Command & Control (C2) communication
- Suspicious outbound connections
- Unauthorized listening services
- Data exfiltration channels
- Lateral movement within the network

---

## Key Network Artifacts

### 1. Active Network Connections

Displays active connections with process IDs and remote IP addresses.

```bash
ss -pant
```

---

### 2. Listening Ports

Shows open ports and services waiting for connections.

```bash
ss -tulnp
```

---

### 3. Network Interfaces

Lists network interfaces and assigned IP addresses.

```bash
ip a
```

---

### 4. Routing Table

Displays network routes and gateways.

```bash
ip route
```

---

### 5. ARP Cache

Shows IP-to-MAC mappings, useful for identifying local network activity.

```bash
arp -a
```

---

### 6. Firewall Rules

Displays firewall rules and packet filtering behavior.

```bash
iptables -L -n -v
```