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