# Memory Acquisition (RAM Forensics)

## Why are we collecting memory?

When a Linux system is compromised, some of the most critical evidence exists in **RAM (volatile memory)**.

Unlike disk data, memory contains the **live execution state of the system**, including running processes, injected code, and active connections. This data is extremely fragile and will be lost immediately if the system is rebooted or powered off.

For this reason, memory acquisition is one of the **highest priority steps** in Linux incident response.

---

## Why Memory Forensics is Critical

Memory analysis allows investigators to uncover:

- **Fileless Malware :** Malicious code executed directly in memory without touching disk
- **Injected Processes :** Attackers may inject payloads into legitimate processes
- **Active Network Connections :** Ongoing communication with attacker infrastructure
- **Credentials & Secrets :** SSH keys, passwords, tokens, and encryption material
- **Decrypted Payloads :** Malware often runs decrypted in RAM even if encrypted on disk

---

## Best Free Tools for Memory Acquisition

### [1. LiME](https://github.com/jtsylve/LiME)

LiME is a widely used Linux kernel module that enables full physical memory acquisition in a forensically sound manner. It supports multiple output formats and can write memory images directly to disk or over the network.

### [2. AVML](https://github.com/microsoft/avml)

AVML is a modern memory acquisition tool designed for Linux environments. It simplifies the dumping process and is well-suited for cloud and virtualized systems.

---

## Memory Acquisition: Physical vs Virtual Systems

Memory acquisition techniques vary significantly depending on whether the system is **physical (bare metal)** or **virtualized (VPS / cloud / VM)**.

This is because access to RAM depends on the **level of control over the hardware and kernel**. Choosing the wrong method can lead to **failed acquisition or loss of critical evidence**.

---

## Acquisition Steps

### Option 1: Using LiME

```bash
insmod lime.ko "path=/mnt/external/memdump.lime format=lime"
```

### Option 2: Using AVML

```bash
sudo ./avml /mnt/external/memdump.lime
```

Allow the process to complete without interacting with the system. Once finished, securely store the memory image for analysis.