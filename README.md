# 🐧 Common Linux Errors & Fixes

## Overview
This document outlines some of the most frequently encountered Linux errors, their causes, and how to resolve them.

---

## 1️⃣ Permission Denied (`Permission denied`)
- **Cause:** Insufficient privileges when accessing files or executing commands.
- **Fix:**
  - Use `sudo` for administrative commands.
  - Check file permissions with `ls -l`.
  - Modify permissions with `chmod` or ownership with `chown`.

## 2️⃣ Command Not Found (`command not found`)
- **Cause:** The command is not installed or not in the system's `$PATH`.
- **Fix:**
  - Install the missing package (`apt install <package>` or `yum install <package>`).
  - Verify `$PATH` with `echo $PATH`.

## 3️⃣ Disk Space Full (`No space left on device`)
- **Cause:** The system has run out of disk space.
- **Fix:**
  - Check disk usage with `df -h`.
  - Identify large files with `du -sh * | sort -h`.
  - Clean logs with `journalctl --vacuum-size=100M`.

## 4️⃣ Too Many Open Files (`Too many open files`)
- **Cause:** The system or a process has hit the file descriptor limit.
- **Fix:**
  - Check current limit with `ulimit -n`.
  - Increase limit with `ulimit -n 65535`.
  - Modify `/etc/security/limits.conf` for a permanent fix.

## 5️⃣ Process Already Running (`Address already in use`)
- **Cause:** A service is already using the required port.
- **Fix:**
  - Identify the process using `netstat -tulnp` or `ss -tulnp`.
  - Stop the process with `kill -9 <PID>`.

## 6️⃣ Dependency Issues (`Unmet dependencies`)
- **Cause:** Package conflicts during installation.
- **Fix:**
  - Run `apt --fix-broken install` (Debian/Ubuntu).
  - Clean package cache with `yum clean all && yum update` (RHEL-based systems).

## 7️⃣ Kernel Panic
- **Cause:** Corrupt system files, bad hardware, or misconfigured kernel parameters.
- **Fix:**
  - Boot into recovery mode.
  - Check logs with `journalctl -xb`.
  - Run `fsck` to fix file system errors.

## 8️⃣ SSH Connection Refused (`Connection refused`)
- **Cause:** SSH service is down, firewall rules, or incorrect port settings.
- **Fix:**
  - Ensure `sshd` is running with `systemctl status ssh`.
  - Check firewall rules with `ufw status` or `iptables -L`.
  - Verify SSH port with `ss -tulnp | grep ssh`.

---

This document serves as a quick reference for troubleshooting common Linux issues. Contributions and updates are welcome! 🐧
