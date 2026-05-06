# User-Level Artifacts

## Why are we analyzing user-level artifacts?

User directories often contain **direct traces of attacker activity.**

Unlike system logs, these artifacts reveal **what commands were executed, what files were accessed, and what tools were used**.

Attackers frequently operate within user contexts, leaving behind valuable evidence in home directories and temporary locations.

---

## Why User Artifact Analysis is Critical

User-level artifacts help investigators uncover:

- Commands executed by attackers
- Downloaded or transferred malicious files
- Tools and scripts used during the attack
- Evidence of lateral movement or data staging
- Interaction with the system (manual or automated)

---

## Common User Artifact Locations

### 1. Bash History

```bash
~/.bash_history
/root/.bash_history
```

---

### 2. Downloaded & Accessed Files

```bash
~/Downloads/
/home/*
```

---

### 3. Temporary Files & Staging Areas

```bash
/tmp
/var/tmp
/dev/shm
```

---

### 4. SSH User Artifacts

```bash
~/.ssh/*
~/.ssh/authorized_keys
~/.ssh/known_hosts
~/.ssh/id_rsa
```

---

### 5. Shell Configuration Files

```bash
~/.bashrc
~/.profile
~/.bash_logout
```
