# Disk Acquisition (Forensic Imaging)

## Why are we collecting disk data?

While memory provides insight into **live activity**, disk data contains the **persistent evidence** left behind by attackers.

This includes files, logs, malware, user activity, and system artifacts that remain available even after the system is powered off.

Disk acquisition ensures you capture a **complete and unaltered copy of the system’s storage**, allowing for in-depth forensic analysis and timeline reconstruction.

---

## Why Disk Forensics is Critical

Disk analysis helps investigators uncover:

- **Malware & Dropped Files :** Executables, scripts, and backdoors stored on disk
- **Persistence Mechanisms :** Cron jobs, services, startup scripts
- **User Activity :** Downloads, command history, accessed files
- **Log Files :** Authentication attempts, system events
- **Deleted Artifacts :** Recoverable traces of attacker actions

---

## Best Tools for Disk Acquisition

### 1. dd (Built-in)

```bash
dd if=/dev/sdX of=/mnt/external/disk.img bs=4M status=progress
```

``dd`` is a native Linux utility used to create a **bit-by-bit** copy of a disk or partition. It is widely available and commonly used in forensic workflows.

### [2. dcfldd](https://github.com/adulau/dcfldd)

```bash
dcfldd if=/dev/sdX of=/mnt/external/disk.img hash=sha256 hashlog=hash.txt
```

``dcfldd`` is an enhanced version of ``dd`` with built-in hashing and logging, making it more suitable for forensic acquisition.

---

## Recommended Method (Step-by-Step)

Start by identifying the correct disk to image:

```bash
lsblk
```

Ensure you have a trusted **external storage device** with enough capacity to store the image.

Run the imaging command (dd or dcfldd) and allow the process to complete without interruption. The duration depends on disk size.

Once finished, calculate and record the hash of the image file to ensure integrity:

```bash
sha256sum /mnt/external/disk.img
```

Store both the image and hash securely for further analysis.