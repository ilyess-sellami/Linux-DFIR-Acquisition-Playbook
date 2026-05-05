# Persistence Investigation

## Why are we investigating persistence?

After gaining initial access, attackers aim to **maintain long-term access** to the system—even after reboots or credential changes.

Persistence mechanisms allow attackers to **re-enter the system silently**, making them one of the most critical aspects to investigate during incident response.

---

## Why Persistence Analysis is Critical

Persistence investigation helps uncover:

- **Backdoors** that allow attackers to reconnect
- **Scheduled malicious tasks** that execute periodically
- **Modified services** that run attacker code
- **Hidden access methods** (SSH keys, startup scripts)
- **Privilege re-escalation paths**

---

## Common Persistence Locations

### 1. Cron Jobs (Scheduled Tasks)

Used to execute commands at scheduled intervals.

```bash
/etc/crontab
/etc/cron.*
/var/spool/cron/
```

**Live Linux check:**

```bash
crontab -l
ls -la /etc/cron*
```

---

### 2. Systemd Services

Attackers may create or modify services to run malicious binaries at startup.

```bash
/etc/systemd/system/
/lib/systemd/system/
```

**Live Linux check:**

```bash
systemctl list-units --type=service
systemctl list-unit-files
```

---

### 3. SSH Persistence (Authorized Keys)

Attackers often add their own SSH key for password-less access.

```bash
~/.ssh/authorized_keys
```

**Live Linux check:**

```bash
cat ~/.ssh/authorized_keys
```

---

### 4. Startup Scripts

Scripts executed during system boot.

```bash
/etc/init.d/
/etc/rc.local
```

**Live Linux check:**

```bash
cat /etc/rc.local
ls -la /etc/init.d/
```

---

### 5. Environment & Profile Files

Attackers may inject malicious commands to execute on user login.

```bash
/etc/profile
~/.bashrc
~/.profile
```

**Live Linux check:**

```bash
cat ~/.bashrc
cat /etc/profile
```

### 6. Suspicious Binaries & Hidden Files

Common attacker staging directories.

```bash
/tmp
/dev/shm
/var/tmp
```

**Live Linux check:**

```bash
ls -la /tmp
ls -la /dev/shm
```