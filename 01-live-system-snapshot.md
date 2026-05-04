# Live System Snapshot (First Response)

## Why are we collecting live system data first?

When a Linux system is compromised, the most critical evidence exists in its **current running state**.

Unlike static disk artifacts, live data reflects **what is happening right now**—including **active processes, network connections, and attacker activity**. This information can quickly disappear if the system is shut down or altered.

This makes live system collection the **first and most time-sensitive step** in a Linux DFIR investigation.

---

## Why Live System Analysis is Critical

Live response helps investigators uncover:

- **Running Malicious Processes :** Attackers often execute tools directly in memory or disguise them as legitimate processes.

- **Active Network Connections :** Ongoing communication with Command & Control (C2) servers can only be observed while the system is live.

- **Logged-in Users & Sessions :** Identifies unauthorized access, SSH sessions, or lateral movement.

- **Open Files & Sockets :** Reveals hidden activity such as backdoors or data exfiltration.

- **Loaded Kernel Modules :** Attackers may use malicious modules to maintain stealth and persistence.

---

## Best Built-in Commands for Live Collection

### 1. Process Enumeration

Displays all running processes with details such as user, PID, CPU, and command:

```bash
ps aux
```

Provides a real-time view of system activity and resource usage:

```bash
top
```

### 2. Network Connections

Lists active listening ports and associated processes:

```bash
ss -tulnp
```

Shows active network connections and remote IP addresses:

```bash
netstat -antp
```

### 3. Logged-in Users

Displays currently logged-in users:

```bash
who
```

Shows active sessions and what users are doing:

```bash
w
```

### 4. Open Files

Lists open files and the processes using them:

```bash
lsof
```

### 5. Kernel Modules

Displays loaded kernel modules:

```bash
lsmod
```

---

## Recommended Approach (Step-by-Step)

Start by collecting a **snapshot of the system state** without interrupting operations. Begin with process enumeration to identify suspicious or unknown binaries. Then, capture active network connections to detect possible communication with external systems.

Next, review logged-in users to identify unauthorized access, followed by open files and sockets to uncover hidden activity. Finally, inspect loaded kernel modules to detect advanced persistence techniques.

All collected data should be **redirected to output files** and stored externally whenever possible. During this phase, avoid modifying the system or executing unnecessary commands to preserve forensic integrity.