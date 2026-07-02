# Linux Commands Cheatsheet for Security

Quick reference for common Linux commands used in pentesting, DevSecOps, and daily security work.

---

## 🔍 Recon & Network

```bash
# Network discovery
nmap -sV -sC -oN scan.txt <target>          # Service + script scan
nmap -p- --min-rate 5000 <target>           # Full port scan (fast)
nmap -sU --top-ports 100 <target>           # UDP scan

# DNS
dig <domain> ANY                             # All DNS records
dig @8.8.8.8 <domain>                       # Query specific resolver
host <domain>
nslookup <domain>

# HTTP
curl -I https://target.com                   # Response headers only
curl -X POST -d '{"key":"val"}' -H "Content-Type: application/json" https://target.com/api
httpie: http GET https://target.com

# Whois / IP lookup
whois <domain>
whois <ip>
```

---

## 📁 File System

```bash
# Find
find / -name "*.conf" 2>/dev/null            # Find config files
find / -perm -4000 2>/dev/null               # SUID binaries (privesc)
find / -writable -type d 2>/dev/null         # Writable directories
find . -name "*.env" -o -name ".env"         # Find .env files

# Grep for secrets
grep -r "password" . --include="*.py"
grep -rE "(api_key|secret|token|password)" . -l
grep -r "BEGIN RSA" . 

# File permissions
chmod 600 file        # Owner read/write only
chmod 755 script.sh   # Owner rwx, others r-x
chown user:group file
```

---

## 🐳 Docker

```bash
# Images
docker images
docker pull ubuntu:22.04
docker rmi <image_id>
docker build -t myapp:v1 .
docker history <image>                       # Layer inspection

# Containers
docker run -it ubuntu bash                   # Interactive
docker run -d -p 8080:80 nginx              # Detached
docker ps -a                                 # All containers
docker exec -it <container_id> bash
docker logs <container_id>
docker stop <container_id>
docker rm <container_id>

# Security scanning
trivy image myapp:latest
docker scout quickview myapp:latest

# Escape check (if in container)
cat /proc/1/cgroup | grep docker            # Are we in a container?
ls /.dockerenv                              # Docker indicator file
```

---

## 🔐 Secrets & Credentials

```bash
# Gitleaks
gitleaks detect --source . --report-format json --report-path leaks.json
gitleaks detect --source . --verbose

# TruffleHog
trufflehog git https://github.com/user/repo
trufflehog filesystem . --only-verified

# Environment
env | grep -i secret
env | grep -i key
printenv
```

---

## 🛡️ File & Process

```bash
# Running processes
ps aux
ps aux | grep python
lsof -i :8080                               # What's listening on port 8080

# Cron jobs (privesc vector)
crontab -l
ls /etc/cron*
cat /etc/crontab

# SUID / SGID (privesc)
find / -perm -u=s -type f 2>/dev/null
find / -perm -g=s -type f 2>/dev/null

# Capabilities
getcap -r / 2>/dev/null
```

---

## 🔑 SSH

```bash
ssh -i key.pem user@host
ssh -L 8080:localhost:80 user@host          # Local port forwarding
ssh -R 8080:localhost:80 user@host          # Remote port forwarding
ssh -D 9050 user@host                       # SOCKS proxy

# Key generation
ssh-keygen -t ed25519 -C "your@email.com"
```

---

## 🐍 Python One-Liners

```bash
# Quick HTTP server
python3 -m http.server 8080

# Reverse shell listener
nc -lvnp 4444

# Base64 decode
echo "dGVzdA==" | base64 -d

# URL decode
python3 -c "import urllib.parse; print(urllib.parse.unquote('hello%20world'))"

# JSON pretty print
cat data.json | python3 -m json.tool

# Generate random password
python3 -c "import secrets, string; print(secrets.token_urlsafe(32))"
```

---

## 🔧 Git Security

```bash
# Check commit author
git log --format="%H %an %ae" -20

# Amend commit email (privacy fix)
git config user.email "ID+user@users.noreply.github.com"
git commit --amend --reset-author --no-edit

# Find secrets in git history
git log --all --full-history -- "*.env"
git grep "password" $(git rev-list --all)

# Signing commits
git config commit.gpgsign true
git log --show-signature
```

---

## 📊 Useful Aliases (add to ~/.bashrc)

```bash
alias ll='ls -alh'
alias ports='netstat -tulanp'
alias myip='curl -s ifconfig.me'
alias dockerclean='docker system prune -af'
alias gits='git status'
alias gitl='git log --oneline -20'
alias scanme='trivy image'
```

---

*Last updated: 2026-07-02*
