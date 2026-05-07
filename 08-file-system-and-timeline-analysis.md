# File System & Timeline Analysis

## Why are we analyzing the file system and timeline?

Attackers leave traces behind through **file creation, modification, execution, and deletion**.

File system analysis helps investigators identify suspicious artifacts, while timeline analysis reconstructs the sequence of attacker actions during the compromise.

Together, they provide a **chronological view of the incident**.

---

## Why Timeline Analysis is Critical

Timeline analysis helps investigators uncover:

- Initial attacker activity
- Malware execution and persistence
- File creation and modification events
- Lateral movement traces
- Data staging and exfiltration activity

---

## Key File System Artifacts

### 1. Recently Modified Files

Identifies files modified within the last 24 hours.

```bash
find / -type f -mtime -1 2>/dev/null
```

---

### 2. File Timestamps (MAC Times)

Displays:

- **M**odified time
- **A**ccessed time
- **C**hanged metadata time

```bash
stat suspicious_file
```

These timestamps help reconstruct attacker activity.

---

### 3. Suspicious Temporary Files

Common Locations:

- ``/tmp``
- ``/var/tmp``
- ``/dev/shm``

Live Linux check:

```bash
find /tmp -type f
find /dev/shm -type f
```

Attackers frequently use these locations to store tools and payloads.

---

### 4. Hidden Files

Searches for hidden files and directories that may contain malicious content.

```bash
find / -name ".*" 2>/dev/null
```

---

### 5. Recently Created Executables

Identifies executable files created or modified recently.

```bash
find / -perm -111 -type f -mtime -7 2>/dev/null
```

---

### 6. File Integrity & Hashing

Generates file hashes for integrity verification and IOC sharing.

```bash
sha256sum suspicious_file
```