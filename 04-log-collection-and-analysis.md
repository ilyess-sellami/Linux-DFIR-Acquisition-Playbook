# Log Collection & Analysis

## Why are logs important?

Logs are one of the most valuable sources of evidence in a Linux investigation. They provide a **historical record of system activity**, allowing investigators to trace attacker actions over time.

Unlike memory (volatile) or disk artifacts (static), logs help answer **who did what, when, and how**.

---

## Why Log Analysis is Critical

Logs help investigators identify:

- **Unauthorized access :** SSH logins, brute-force attempts
- **Privilege escalation :** ``sudo`` usage, user switching
- **Service activity :** Web servers, cron jobs, daemons
- **System changes :** Reboots, configuration changes
- **Attacker behavior :** Commands executed, persistence actions

---

## Key Log Locations

### 1. Authentication & Access Logs

SSH logins, failed attempts, and sudo activity:

```bash
/var/log/auth.log (Debian/Ubuntu)
```

Authentication events and privilege escalation:

```bash
/var/log/secure (RHEL/CentOS)
```

Failed login attempts per user:

```bash
/var/log/faillog
```

Last login information for all users:

```bash
/var/log/lastlog
```

Historical login/logout sessions:

```bash
/var/log/wtmp
```

Failed login attempts (binary log):

```bash
/var/log/btmp
```

---

### 2. System & Kernel Logs

General system activity and service logs:

```bash
/var/log/syslog
```

System and kernel messages:

```bash
/var/log/messages
```

Kernel ring buffer (boot and hardware events):

```bash
/var/log/dmesg
```

Kernel-specific logs (if enabled):

```bash
/var/log/kern.log
```

---

### 3. Web Server Logs

Apache:

```bash
/var/log/apache2/access.log
/var/log/apache2/error.log
```

Nginx:

```bash
/var/log/nginx/access.log
/var/log/nginx/error.log
```

---

### 4. Package & Installation Logs

Installed/removed packages:

```bash
/var/log/apt/history.log
/var/log/yum.log (RHEL/CentOS)
```

Detailed package installation output

```bash
/var/log/apt/term.log
```

Modern package manager logs:

```bash
/var/log/dnf.log
```

---

## 5. Scheduled Tasks & Cron Logs

```bash
/var/log/cron
```

---

## 6. Security & Firewall Logs

Allowed/blocked traffic:

```bash
/var/log/ufw.log
```

Banned IPs and intrusion prevention actions:

```bash
/var/log/fail2ban.log
```

---

### 7. User Activity Logs

Commands executed by users:

```bash
~/.bash_history
```

Root user command history:

```bash
/root/.bash_history
```

---

### 8. Network & Service Logs

Mail server activity (possible exfiltration):

```bash
/var/log/mail.log
```

FTP access and file transfers:

```bash
/var/log/vsftpd.log
```

SMB file sharing activity:

```bash
/var/log/samba/
```
