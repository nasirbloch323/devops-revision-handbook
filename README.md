# 🚀 DevOps Interview Revision Notes (Beginner → Interview Ready)

> Daily revision notes for **DevOps Internship / Junior DevOps** interviews.
> Har topic mein: **Concept → Why → Commands (category-wise) → Example → Interview Questions**.

**Author:** Nasir Mehmood

---

## 📑 Index

| No. | Topic |
|-----|-------|
| 1 | [DevOps Basics](#1-devops-basics) |
| 2 | [Linux](#2-linux) |
| 3 | [Bash Scripting](#3-bash-scripting) |
| 4 | [Networking Basics](#4-networking-basics) |
| 5 | [Git & GitHub](#5-git--github) |
| 6 | [Docker](#6-docker) |
| 7 | [Kubernetes](#7-kubernetes) |
| 8 | [Terraform](#8-terraform) |
| 9 | [Ansible](#9-ansible) |
| 10 | [Jenkins](#10-jenkins) |
| 11 | [GitHub Actions](#11-github-actions) |
| 12 | [ArgoCD & GitOps](#12-argocd--gitops) |
| 13 | [Monitoring (Prometheus & Grafana)](#13-monitoring-prometheus--grafana) |
| 14 | [AWS / Cloud Basics](#14-aws--cloud-basics) |
| 15 | [Common Interview Questions (Rapid Fire)](#15-common-interview-questions-rapid-fire) |
| 16 | [Daily Revision Plan](#16-daily-revision-plan) |

---

# 1. DevOps Basics

## 1.1 What is DevOps?
**DevOps = Development + Operations.** It is a culture + set of practices where developers and operations teams work together to **build, test, and release software faster and more reliably**.

**Simple example:** Pehle developer code likh ke ops team ko dete the, ops deploy karte the, aur bugs pe dono ek doosre ko blame karte the. DevOps mein dono ek team hain, aur process **automated** hota hai.

## 1.2 Why DevOps?
- Faster releases (daily/hourly instead of monthly)
- Fewer bugs in production (automated testing)
- Quick recovery when something fails
- Automation removes manual mistakes

## 1.3 DevOps Lifecycle (infinity loop)
```
Plan → Code → Build → Test → Release → Deploy → Operate → Monitor → (back to Plan)
```
| Stage | Tools |
|-------|-------|
| Plan | Jira, Trello |
| Code | Git, GitHub, GitLab |
| Build | Maven, npm, Docker |
| Test | JUnit, Selenium, SonarQube |
| Release/CI-CD | Jenkins, GitHub Actions, GitLab CI |
| Deploy | Kubernetes, ArgoCD, Ansible |
| Infra | Terraform, CloudFormation |
| Monitor | Prometheus, Grafana, ELK |

## 1.4 Key Terms
| Term | Meaning | Example |
|------|---------|---------|
| **CI** (Continuous Integration) | Developers merge code often; every push is auto built + tested | Push code → Jenkins runs tests |
| **CD** (Continuous Delivery) | Code is always ready to deploy; release needs manual approval | Build ready, click "Deploy" |
| **CD** (Continuous Deployment) | Every passing change goes to production automatically | No human approval |
| **IaC** (Infrastructure as Code) | Servers/networks created by code, not by clicking | Terraform creates EC2 |
| **Configuration Management** | Configure many servers consistently | Ansible installs nginx on 50 servers |
| **GitOps** | Git is the single source of truth for infra/deployments | ArgoCD syncs Git → Kubernetes |
| **Containerization** | Package app + dependencies together | Docker |
| **Orchestration** | Manage many containers automatically | Kubernetes |
| **Monitoring** | Watch system health | Prometheus |
| **Pipeline** | Automated steps from code to production | Build → Test → Deploy |

## 1.5 CI/CD Pipeline Example
```
Developer pushes code to GitHub
        ↓
Jenkins/GitHub Actions triggers
        ↓
Build (compile / docker build)
        ↓
Test (unit tests)
        ↓
Push Docker image to Docker Hub/ECR
        ↓
Deploy to Kubernetes (ArgoCD / kubectl)
        ↓
Monitor (Prometheus + Grafana)
```

## 1.6 Interview Questions
1. **What is DevOps?** → Culture + practices combining dev & ops using automation for fast, reliable delivery.
2. **Difference between CI and CD?** → CI = auto build/test on every commit. CD = auto release/deploy.
3. **Continuous Delivery vs Deployment?** → Delivery needs manual approval; Deployment is fully automatic.
4. **What is IaC? Benefits?** → Infra defined in code: repeatable, version-controlled, fast, less human error.
5. **Agile vs DevOps?** → Agile = how to develop (sprints). DevOps = how to deliver/operate (automation, CI/CD).
6. **What is a pipeline?** → Automated sequence of stages (build, test, deploy).
7. **What is shift-left?** → Doing testing/security early in the cycle.

---

# 2. Linux

## 2.1 What is Linux?
Linux is an **open-source operating system kernel**. Almost all servers, cloud VMs, and containers run Linux, so DevOps engineers *must* know it.

- **Kernel** = core of OS (talks to hardware)
- **Shell** = program that takes your commands (bash, zsh)
- **Distribution (distro)** = Kernel + tools (Ubuntu, CentOS, RHEL, Debian, Amazon Linux)

## 2.2 Linux Directory Structure
| Directory | Purpose |
|-----------|---------|
| `/` | Root of everything |
| `/home` | Users' personal folders |
| `/root` | Home of root user |
| `/etc` | **Configuration files** (nginx, ssh, passwd) |
| `/var` | Variable data — **logs** in `/var/log` |
| `/bin`, `/usr/bin` | User commands (ls, cat) |
| `/sbin` | System/admin commands |
| `/tmp` | Temporary files |
| `/opt` | Optional/third-party software |
| `/dev` | Device files |
| `/proc` | Running process & kernel info (virtual) |
| `/mnt`, `/media` | Mount points |

## 2.3 Commands by Category

### 📂 File & Directory
| Command | Use | Example |
|---------|-----|---------|
| `pwd` | Show current directory | `pwd` |
| `ls -la` | List all files with details | `ls -lah` |
| `cd` | Change directory | `cd /var/log`, `cd ..`, `cd ~` |
| `mkdir -p` | Create directory (nested) | `mkdir -p app/logs` |
| `touch` | Create empty file | `touch a.txt` |
| `cp -r` | Copy | `cp -r src/ backup/` |
| `mv` | Move/rename | `mv old.txt new.txt` |
| `rm -rf` | Delete (⚠️ dangerous) | `rm -rf test/` |
| `cat` | Show file | `cat /etc/os-release` |
| `less` | Scroll through file | `less app.log` |
| `head -n 5` / `tail -n 5` | First/last lines | `tail -f app.log` (live logs) |
| `find` | Search files | `find / -name "*.log"` |
| `ln -s` | Symbolic link | `ln -s /opt/app /app` |
| `tree` | Show directory tree | `tree -L 2` |

### 📝 Text Processing (VERY important)
| Command | Use | Example |
|---------|-----|---------|
| `grep` | Search text | `grep -i "error" app.log` |
| `grep -r` | Search recursively | `grep -r "password" /etc` |
| `grep -v` | Exclude matches | `grep -v "INFO" app.log` |
| `awk` | Column processing | `awk '{print $1}' file` |
| `sed` | Find & replace | `sed -i 's/old/new/g' file` |
| `cut` | Cut columns | `cut -d: -f1 /etc/passwd` |
| `sort` / `uniq` | Sort / remove duplicates | `sort file \| uniq -c` |
| `wc -l` | Count lines | `wc -l file` |
| `tr` | Translate chars | `echo hi \| tr a-z A-Z` |
| `diff` | Compare files | `diff a.txt b.txt` |

**Pipe `|`** sends output of one command to another:
```bash
# Top 5 IPs hitting the server
cat access.log | awk '{print $1}' | sort | uniq -c | sort -nr | head -5
```
**Redirection:** `>` overwrite, `>>` append, `2>` errors, `&>` both.
```bash
ls > files.txt          # overwrite
echo "hi" >> files.txt  # append
cmd 2> error.log        # errors only
```

### 👤 Users & Groups
| Command | Use |
|---------|-----|
| `whoami`, `id` | Current user info |
| `useradd -m nasir` | Create user with home |
| `passwd nasir` | Set password |
| `usermod -aG docker nasir` | Add user to group |
| `userdel -r nasir` | Delete user |
| `groupadd devs` | Create group |
| `su - nasir` | Switch user |
| `sudo cmd` | Run as root |

Files: `/etc/passwd` (users), `/etc/shadow` (passwords), `/etc/group` (groups), `/etc/sudoers` (sudo rights; edit with `visudo`).

### 🔐 Permissions (VERY important)
```
-rwxr-xr--   1 nasir devs  file.sh
 │└┬┘└┬┘└┬┘
 │ │  │  └─ Others: r--  (4)
 │ │  └──── Group:  r-x  (5)
 │ └─────── Owner:  rwx  (7)
 └───────── Type: - file, d directory, l link
```
**r=4, w=2, x=1.**

| Command | Example |
|---------|---------|
| `chmod 755 file` | Owner rwx, others r-x |
| `chmod +x script.sh` | Make executable |
| `chmod -R 644 dir/` | Recursive |
| `chown user:group file` | Change owner |
| `chown -R nasir:devs /app` | Recursive |

Common: `777` full access (⚠️ unsafe), `755` scripts/dirs, `644` normal files, `600` private keys (SSH keys MUST be 600/400).

**Special permissions:** SUID (`4xxx`), SGID (`2xxx`), Sticky bit (`1xxx`, e.g. `/tmp`).

### ⚙️ Process Management
| Command | Use |
|---------|-----|
| `ps aux` | All running processes |
| `ps -ef \| grep nginx` | Find a process |
| `top` / `htop` | Live resource usage |
| `kill PID` | Stop (SIGTERM, 15) |
| `kill -9 PID` | Force kill (SIGKILL) |
| `pkill nginx` | Kill by name |
| `bg` / `fg` / `jobs` | Background/foreground jobs |
| `nohup cmd &` | Run even after logout |
| `nice` / `renice` | Process priority |

**Process states:** Running, Sleeping, Stopped, **Zombie** (finished but parent didn't read exit status).

### 💾 Disk & Memory
| Command | Use |
|---------|-----|
| `df -h` | Disk space of filesystems |
| `du -sh *` | Size of folders |
| `free -h` | RAM usage |
| `lsblk` | List block devices |
| `fdisk -l` | Partitions |
| `mount` / `umount` | Mount/unmount disk |
| `uptime` | Load average |
| `vmstat`, `iostat` | Performance stats |

### 🌐 Networking
| Command | Use |
|---------|-----|
| `ip a` (or `ifconfig`) | IP addresses |
| `ping google.com` | Check connectivity |
| `curl -I url` | HTTP request/headers |
| `wget url` | Download file |
| `ss -tulnp` (or `netstat -tulnp`) | Open ports + process |
| `nslookup` / `dig` | DNS lookup |
| `traceroute` | Path to host |
| `ssh user@ip` | Remote login |
| `scp file user@ip:/path` | Copy over SSH |
| `rsync -avz src dest` | Efficient sync |
| `telnet ip port` / `nc -zv ip port` | Test port |

### 📦 Package Management
| Distro | Commands |
|--------|----------|
| Ubuntu/Debian | `apt update`, `apt install nginx`, `apt remove nginx` |
| RHEL/CentOS | `yum install nginx` / `dnf install nginx` |

### 🔧 Services (systemd)
```bash
systemctl start nginx       # start
systemctl stop nginx        # stop
systemctl restart nginx     # restart
systemctl status nginx      # check status
systemctl enable nginx      # start at boot
systemctl disable nginx
journalctl -u nginx -f      # service logs (live)
```

### 📜 Logs
| File | Content |
|------|---------|
| `/var/log/syslog` (Ubuntu) / `/var/log/messages` (RHEL) | System log |
| `/var/log/auth.log` | Login/SSH attempts |
| `/var/log/nginx/` | Nginx logs |
| `dmesg` | Kernel messages |

### 🗜️ Archive
```bash
tar -cvf a.tar dir/        # create
tar -czvf a.tar.gz dir/    # create + gzip
tar -xzvf a.tar.gz         # extract
zip -r a.zip dir/ ; unzip a.zip
```

### ⏰ Cron (scheduling)
```bash
crontab -e      # edit
crontab -l      # list
# ┌ min ┌ hour ┌ day ┌ month ┌ weekday
  0     2      *     *       *      /scripts/backup.sh   # daily 2 AM
  */5   *      *     *       *      /scripts/check.sh    # every 5 min
```

### 🛡️ Firewall & SSH
```bash
ufw allow 22 ; ufw enable ; ufw status      # Ubuntu
firewall-cmd --add-port=80/tcp --permanent  # RHEL
ssh-keygen -t rsa -b 4096                   # generate key
ssh-copy-id user@ip                         # passwordless login
```
SSH config: `/etc/ssh/sshd_config` (disable root login, password auth for security).

## 2.4 Example: Troubleshooting a slow server
```bash
uptime            # check load
top               # which process uses CPU?
free -h           # memory ok?
df -h             # disk full?
tail -f /var/log/syslog   # any errors?
ss -tulnp         # ports ok?
```

## 2.5 Interview Questions
1. **Hard link vs Soft link?** → Hard link = another name for same inode (works if original deleted). Soft link = shortcut to path (breaks if original deleted).
2. **What is inode?** → Data structure storing file metadata (owner, size, permissions, block location) — not the filename.
3. **`kill` vs `kill -9`?** → kill = polite stop (SIGTERM), -9 = force kill (SIGKILL), process can't clean up.
4. **How to check which process uses port 80?** → `ss -tulnp | grep :80` or `lsof -i :80`.
5. **Disk full — how to find culprit?** → `df -h`, then `du -sh /* | sort -h`.
6. **What is load average?** → Average number of processes waiting for CPU over 1, 5, 15 min.
7. **What is a zombie process?** → Finished process whose parent hasn't collected its status.
8. **grep vs find?** → grep searches *inside* files; find searches for *files*.
9. **What is sudo?** → Run a command with root/other user privileges.
10. **What is swap?** → Disk space used as extra RAM when RAM is full.
11. **Difference between `/etc/passwd` and `/etc/shadow`?** → passwd = user info (public); shadow = encrypted passwords (root-only).
12. **What happens at Linux boot?** → BIOS/UEFI → Bootloader (GRUB) → Kernel → systemd (init) → Services.
13. **What is `chmod 755`?** → Owner rwx, group r-x, others r-x.
14. **What is a daemon?** → Background service process (e.g. sshd, nginx).

---

# 3. Bash Scripting

## 3.1 What is it?
Bash script = a text file with Linux commands, run top to bottom. Used to **automate** repetitive tasks (backup, deploy, health checks).

First line is the **shebang**: `#!/bin/bash`. Run it: `chmod +x script.sh && ./script.sh`

## 3.2 Basics
```bash
#!/bin/bash
# This is a comment

name="Nasir"                 # variable (no spaces around =)
echo "Hello $name"           # use variable
echo "Today: $(date)"        # command substitution

read -p "Enter age: " age    # user input
echo "Args: $1 $2"           # command-line arguments
```

### Special Variables
| Variable | Meaning |
|----------|---------|
| `$0` | Script name |
| `$1 $2 ...` | Arguments |
| `$#` | Number of arguments |
| `$@` | All arguments |
| `$?` | Exit status of last command (0 = success) |
| `$$` | PID of script |

## 3.3 Conditions
```bash
if [ $age -ge 18 ]; then
  echo "Adult"
elif [ $age -gt 12 ]; then
  echo "Teen"
else
  echo "Child"
fi
```
| Test | Meaning |
|------|---------|
| `-eq -ne -gt -lt -ge -le` | Number compare |
| `==  !=` | String compare |
| `-f file` | File exists |
| `-d dir` | Directory exists |
| `-z str` | String empty |
| `-x file` | Executable |

## 3.4 Loops
```bash
for i in 1 2 3; do echo $i; done

for file in *.log; do echo "Processing $file"; done

count=1
while [ $count -le 5 ]; do
  echo $count
  ((count++))
done
```

## 3.5 Functions
```bash
greet() {
  echo "Hello $1"
}
greet "Ali"
```

## 3.6 Real DevOps Examples

**Example 1 – Check if service is running**
```bash
#!/bin/bash
SERVICE=nginx
if systemctl is-active --quiet $SERVICE; then
  echo "$SERVICE is running"
else
  echo "$SERVICE is down, restarting..."
  systemctl restart $SERVICE
fi
```

**Example 2 – Disk usage alert**
```bash
#!/bin/bash
USAGE=$(df / | awk 'NR==2 {print $5}' | tr -d '%')
if [ $USAGE -gt 80 ]; then
  echo "WARNING: Disk usage is ${USAGE}%"
fi
```

**Example 3 – Backup with date**
```bash
#!/bin/bash
tar -czf /backup/app_$(date +%F).tar.gz /var/www/app
find /backup -mtime +7 -delete     # delete backups older than 7 days
```

## 3.7 Good Practices
```bash
set -e          # exit on any error
set -u          # error on undefined variable
set -o pipefail # fail if any command in pipe fails
```
Always quote variables: `"$var"`.

## 3.8 Interview Questions
1. **What is shebang?** → `#!/bin/bash` — tells which interpreter runs the script.
2. **`$?` meaning?** → Exit code of last command; 0 = success, non-zero = failure.
3. **`$@` vs `$*`?** → `"$@"` treats each argument separately; `"$*"` joins all as one string.
4. **How do you debug a script?** → `bash -x script.sh` or `set -x`.
5. **Single vs double quotes?** → Double expands variables, single treats as literal.
6. **How to run script in background?** → `./script.sh &` or `nohup ./script.sh &`.
7. **What does `set -e` do?** → Stops script on first error.

---

# 4. Networking Basics

| Concept | Explanation |
|---------|-------------|
| **IP Address** | Unique address of device (IPv4: `192.168.1.10`) |
| **Public vs Private IP** | Private ranges: `10.x.x.x`, `172.16–31.x.x`, `192.168.x.x` |
| **Subnet / CIDR** | `192.168.1.0/24` = 256 IPs (254 usable) |
| **Port** | Door number for service: SSH 22, HTTP 80, HTTPS 443, MySQL 3306, PostgreSQL 5432, Jenkins 8080, Kubernetes API 6443 |
| **DNS** | Converts name → IP (google.com → 142.x.x.x) |
| **DHCP** | Auto-assigns IPs |
| **NAT** | Lets private IPs access internet via one public IP |
| **Gateway** | Router exit to other networks |
| **Firewall** | Allows/blocks traffic by rules |
| **Load Balancer** | Distributes traffic across servers |
| **Reverse Proxy** | Sits before servers, forwards requests (nginx) |
| **VPN** | Secure tunnel over internet |

**TCP vs UDP:** TCP = reliable, connection-based (web, SSH). UDP = fast, no guarantee (video, DNS).

**OSI Model (7 layers):** Physical, Data Link, Network (IP), Transport (TCP/UDP), Session, Presentation, Application (HTTP).

**HTTP codes:** 200 OK, 301 redirect, 401 unauthorized, 403 forbidden, 404 not found, 500 server error, 502 bad gateway, 503 unavailable.

**What happens when you type google.com?** DNS lookup → TCP connection → TLS handshake (HTTPS) → HTTP request → Server response → Browser renders.

---

# 5. Git & GitHub

## 5.1 What is Git?
Git is a **distributed version control system** — tracks changes in code, lets many people work together, and lets you go back to any old version.
- **Git** = tool on your computer. **GitHub/GitLab/Bitbucket** = websites that host Git repos.

## 5.2 Three Areas
```
Working Directory → (git add) → Staging Area → (git commit) → Local Repo → (git push) → Remote Repo
```

## 5.3 Commands by Category

### Setup
```bash
git config --global user.name "Nasir"
git config --global user.email "me@mail.com"
git init                      # new repo
git clone <url>               # copy remote repo
```

### Basic Workflow
| Command | Use |
|---------|-----|
| `git status` | See changed files |
| `git add file` / `git add .` | Stage changes |
| `git commit -m "msg"` | Save snapshot |
| `git push origin main` | Upload |
| `git pull` | Download + merge |
| `git fetch` | Download only (no merge) |
| `git log --oneline --graph` | History |
| `git diff` | See changes |
| `git show <commit>` | Details of commit |

### Branching
```bash
git branch                  # list
git branch feature-x        # create
git checkout feature-x      # switch  (or: git switch feature-x)
git checkout -b feature-x   # create + switch
git merge feature-x         # merge into current branch
git branch -d feature-x     # delete
```

### Undo / Fix Mistakes
| Situation | Command |
|-----------|---------|
| Unstage a file | `git restore --staged file` |
| Discard local changes | `git restore file` |
| Fix last commit message | `git commit --amend` |
| Undo commit, keep changes | `git reset --soft HEAD~1` |
| Undo commit, discard changes | `git reset --hard HEAD~1` ⚠️ |
| Safe undo (new reverse commit) | `git revert <commit>` |
| Save work temporarily | `git stash` / `git stash pop` |
| Copy one commit | `git cherry-pick <commit>` |
| Find lost commits | `git reflog` |

### Remote
```bash
git remote -v
git remote add origin <url>
git push -u origin main
git push origin --delete branch
```

### Tags
```bash
git tag v1.0
git push origin v1.0
```

## 5.4 Merge vs Rebase
- **Merge:** joins branches, creates merge commit, keeps full history.
- **Rebase:** replays your commits on top of another branch, gives linear/clean history. ⚠️ Never rebase shared/public branches.

## 5.5 Merge Conflict
Happens when two people change the same line. Git marks it:
```
<<<<<<< HEAD
your change
=======
their change
>>>>>>> feature-x
```
Fix: edit file → keep correct code → `git add file` → `git commit`.

## 5.6 Branching Strategies
- **Git Flow:** main, develop, feature, release, hotfix
- **GitHub Flow:** main + short feature branches + Pull Requests
- **Trunk-based:** everyone commits to main frequently

## 5.7 .gitignore
File that lists what Git should ignore: `node_modules/`, `.env`, `*.log`, `.terraform/`.

## 5.8 Example – Typical day
```bash
git checkout -b feature-login
# ...write code...
git add .
git commit -m "Add login page"
git push origin feature-login
# Open Pull Request on GitHub → review → merge
```

## 5.9 Interview Questions
1. **Git vs GitHub?** → Git is VCS tool; GitHub is hosting platform.
2. **`git pull` vs `git fetch`?** → pull = fetch + merge; fetch only downloads.
3. **`reset` vs `revert`?** → reset rewrites history; revert adds a new commit that undoes (safe for shared branches).
4. **`merge` vs `rebase`?** → See 5.4.
5. **What is `git stash`?** → Temporarily saves uncommitted changes.
6. **What is HEAD?** → Pointer to current commit/branch.
7. **What is a fork?** → Your own copy of someone's repo on GitHub.
8. **What is a Pull Request?** → Request to merge your branch, with review.
9. **How to undo a pushed commit?** → `git revert`.
10. **What is `git cherry-pick`?** → Apply a specific commit to current branch.
11. **How to remove a secret committed by mistake?** → Rotate the secret first, then remove from history (`git filter-repo`/BFG).
12. **What is detached HEAD?** → HEAD points to a commit, not a branch.

---

# 6. Docker

## 6.1 What is Docker?
Docker packages an application **with all its dependencies** into a **container**, so it runs the same everywhere ("works on my machine" problem solved).

## 6.2 Container vs Virtual Machine
| | Container | VM |
|---|-----------|----|
| Shares host OS kernel | ✅ | ❌ (own OS) |
| Size | MBs | GBs |
| Startup | Seconds | Minutes |
| Isolation | Process-level | Full |

## 6.3 Key Concepts
| Term | Meaning |
|------|---------|
| **Image** | Read-only template (like a recipe/blueprint) |
| **Container** | Running instance of an image |
| **Dockerfile** | Text file with steps to build an image |
| **Registry** | Storage for images (Docker Hub, ECR, GCR) |
| **Volume** | Persistent storage outside container |
| **Network** | Communication between containers |
| **Docker Engine/Daemon** | Background service that runs containers |
| **Layers** | Each Dockerfile instruction = a cached layer |

## 6.4 Commands by Category

### Images
| Command | Use |
|---------|-----|
| `docker pull nginx` | Download image |
| `docker images` | List images |
| `docker build -t myapp:1.0 .` | Build image |
| `docker tag myapp:1.0 user/myapp:1.0` | Tag |
| `docker push user/myapp:1.0` | Upload |
| `docker rmi image` | Remove image |
| `docker image prune` | Remove unused |

### Containers
| Command | Use |
|---------|-----|
| `docker run -d -p 8080:80 --name web nginx` | Run in background, map port |
| `docker ps` / `docker ps -a` | Running / all containers |
| `docker stop web` / `start` / `restart` | Control |
| `docker rm web` / `docker rm -f web` | Remove |
| `docker logs -f web` | View logs |
| `docker exec -it web bash` | Enter container |
| `docker inspect web` | Full details |
| `docker stats` | Live CPU/RAM |
| `docker cp file web:/path` | Copy file |

**`docker run` flags:** `-d` detached, `-p host:container` port, `-v` volume, `-e KEY=val` env var, `--name`, `--rm` auto-delete, `--network`, `-it` interactive.

### Volumes & Networks
```bash
docker volume create mydata
docker run -v mydata:/var/lib/mysql mysql          # named volume
docker run -v $(pwd):/app node                     # bind mount
docker network create mynet
docker run --network mynet --name db mysql
```

### Cleanup
```bash
docker system prune -a      # remove everything unused ⚠️
```

## 6.5 Dockerfile
| Instruction | Meaning |
|-------------|---------|
| `FROM` | Base image |
| `WORKDIR` | Set working dir |
| `COPY` / `ADD` | Copy files (ADD can also extract tar/URL) |
| `RUN` | Execute command **during build** |
| `CMD` | Default command **at runtime** (can be overridden) |
| `ENTRYPOINT` | Fixed command at runtime |
| `ENV` | Environment variable |
| `EXPOSE` | Document port |
| `ARG` | Build-time variable |
| `USER` | Run as non-root |

**Example – Node.js app:**
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["node", "server.js"]
```
Build & run:
```bash
docker build -t myapp:1.0 .
docker run -d -p 3000:3000 myapp:1.0
```
💡 Copy `package.json` first, then code → so `npm install` layer is **cached** when only code changes.

### Multi-stage build (smaller image)
```dockerfile
FROM maven:3.9 AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM openjdk:17-slim
COPY --from=build /app/target/app.jar /app.jar
CMD ["java", "-jar", "/app.jar"]
```

## 6.6 Docker Compose
Run **multiple containers** with one file (`docker-compose.yml`):
```yaml
version: "3.8"
services:
  web:
    build: .
    ports:
      - "8080:5000"
    depends_on:
      - db
    environment:
      - DB_HOST=db
  db:
    image: postgres:15
    environment:
      POSTGRES_PASSWORD: secret
    volumes:
      - dbdata:/var/lib/postgresql/data
volumes:
  dbdata:
```
```bash
docker compose up -d     # start all
docker compose ps
docker compose logs -f
docker compose down      # stop & remove
```

## 6.7 Networking Types
`bridge` (default, containers on same host), `host` (shares host network), `none` (no network), `overlay` (multi-host, Swarm).

## 6.8 Best Practices
- Use small base images (alpine, slim)
- Multi-stage builds
- Don't run as root (`USER`)
- Use `.dockerignore`
- Pin versions (`node:18`, not `latest`)
- Don't put secrets in image
- One process per container

## 6.9 Interview Questions
1. **Container vs VM?** → See 6.2.
2. **Image vs Container?** → Image = blueprint; container = running instance.
3. **CMD vs ENTRYPOINT?** → CMD = default args, easily overridden; ENTRYPOINT = main executable, always runs.
4. **COPY vs ADD?** → ADD can extract archives & fetch URLs; prefer COPY.
5. **How to persist data?** → Volumes / bind mounts.
6. **How to reduce image size?** → Alpine/slim base, multi-stage builds, fewer layers, .dockerignore.
7. **Container exits immediately — why?** → Main process finished/crashed. Check `docker logs`.
8. **How do containers communicate?** → Same user-defined network, using container name as DNS.
9. **What is Docker layer caching?** → Unchanged layers are reused for faster builds.
10. **Docker vs Docker Compose?** → Docker = single container; Compose = multi-container apps.
11. **What is Docker Swarm?** → Docker's built-in orchestrator (Kubernetes is more popular).
12. **Volume vs bind mount?** → Volume managed by Docker; bind mount maps a host path.
13. **How to see why a container is failing?** → `docker logs`, `docker inspect`, `docker exec`.
14. **What are namespaces & cgroups?** → Namespaces = isolation (process, network); cgroups = resource limits (CPU, RAM).

---

# 7. Kubernetes

## 7.1 What is Kubernetes (K8s)?
Kubernetes is a **container orchestration platform**. Docker runs 1 container; Kubernetes runs **hundreds**, and automatically handles:
- **Self-healing** (restarts crashed containers)
- **Scaling** (more/less pods by load)
- **Load balancing**
- **Rolling updates & rollbacks** (zero downtime)
- **Service discovery**

## 7.2 Architecture
```
              ┌──────────── Control Plane (Master) ────────────┐
              │ API Server | etcd | Scheduler | Controller Mgr │
              └────────────────────────┬───────────────────────┘
                                       │
          ┌────────────────────────────┴──────────────┐
   ┌──── Worker Node 1 ────┐                  ┌──── Worker Node 2 ────┐
   │ kubelet | kube-proxy  │                  │ kubelet | kube-proxy  │
   │ Container runtime     │                  │ Container runtime     │
   │ [Pod] [Pod]           │                  │ [Pod] [Pod]           │
   └───────────────────────┘                  └───────────────────────┘
```
| Component | Role |
|-----------|------|
| **API Server** | Front door; all `kubectl` commands go here |
| **etcd** | Key-value DB storing cluster state |
| **Scheduler** | Decides which node runs a new pod |
| **Controller Manager** | Keeps desired state = actual state |
| **kubelet** | Agent on node; runs pods |
| **kube-proxy** | Networking rules on node |
| **Container Runtime** | Runs containers (containerd) |

## 7.3 Core Objects
| Object | Meaning |
|--------|---------|
| **Pod** | Smallest unit; 1+ containers sharing network/storage |
| **ReplicaSet** | Keeps N pod replicas running |
| **Deployment** | Manages ReplicaSets; rolling updates/rollback (most used) |
| **Service** | Stable IP/DNS to access pods |
| **Namespace** | Virtual cluster for isolation (dev/prod) |
| **ConfigMap** | Non-secret config |
| **Secret** | Sensitive data (base64 encoded) |
| **Ingress** | HTTP/HTTPS routing from outside (host/path based) |
| **PV / PVC** | Persistent storage / request for storage |
| **StatefulSet** | For stateful apps (DB) with stable identity |
| **DaemonSet** | One pod on every node (logging agents) |
| **Job / CronJob** | One-time / scheduled tasks |
| **HPA** | Horizontal Pod Autoscaler |
| **Node** | A worker machine |

### Service Types
| Type | Use |
|------|-----|
| **ClusterIP** (default) | Internal only |
| **NodePort** | Exposes on node IP:30000-32767 |
| **LoadBalancer** | Cloud load balancer (external) |
| **ExternalName** | Maps to external DNS |

## 7.4 kubectl Commands by Category

### Cluster Info
```bash
kubectl cluster-info
kubectl get nodes -o wide
kubectl version
```

### Get / Describe
```bash
kubectl get pods
kubectl get pods -A                     # all namespaces
kubectl get pods -n dev -o wide
kubectl get all
kubectl get deploy,svc,ing
kubectl describe pod mypod              # events! best for debugging
```

### Create / Apply / Delete
```bash
kubectl apply -f deployment.yaml        # create/update (declarative)
kubectl create deployment web --image=nginx
kubectl delete -f deployment.yaml
kubectl delete pod mypod
kubectl run test --image=nginx          # quick pod
```

### Debugging
```bash
kubectl logs mypod
kubectl logs mypod -c container1 -f     # specific container, follow
kubectl logs mypod --previous           # logs of crashed container
kubectl exec -it mypod -- /bin/bash
kubectl port-forward pod/mypod 8080:80
kubectl top pods                        # CPU/memory
kubectl get events --sort-by=.metadata.creationTimestamp
```

### Scaling & Updates
```bash
kubectl scale deployment web --replicas=5
kubectl set image deployment/web nginx=nginx:1.25
kubectl rollout status deployment/web
kubectl rollout history deployment/web
kubectl rollout undo deployment/web     # rollback
kubectl autoscale deployment web --min=2 --max=10 --cpu-percent=70
```

### Config
```bash
kubectl config get-contexts
kubectl config use-context mycluster
kubectl create configmap app-config --from-literal=ENV=prod
kubectl create secret generic db-pass --from-literal=password=abc123
kubectl edit deployment web
kubectl explain pod.spec
```

## 7.5 YAML Examples

**Deployment**
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: web
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web
  template:
    metadata:
      labels:
        app: web
    spec:
      containers:
      - name: nginx
        image: nginx:1.25
        ports:
        - containerPort: 80
        resources:
          requests: { cpu: "100m", memory: "128Mi" }
          limits:   { cpu: "250m", memory: "256Mi" }
        livenessProbe:
          httpGet: { path: /, port: 80 }
        readinessProbe:
          httpGet: { path: /, port: 80 }
```

**Service**
```yaml
apiVersion: v1
kind: Service
metadata:
  name: web-svc
spec:
  type: NodePort
  selector:
    app: web          # matches pod labels
  ports:
  - port: 80          # service port
    targetPort: 80    # container port
    nodePort: 30080
```

**Ingress**
```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: web-ingress
spec:
  rules:
  - host: myapp.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: web-svc
            port:
              number: 80
```

## 7.6 Important Concepts
- **Labels & Selectors:** key/value tags; Services find pods via labels.
- **Probes:** *Liveness* = is container alive? (restart if fails). *Readiness* = ready for traffic? (remove from service if fails). *Startup* = slow-starting apps.
- **Requests vs Limits:** request = guaranteed minimum; limit = maximum allowed.
- **Rolling update:** replaces pods gradually → zero downtime.
- **RBAC:** Role-Based Access Control (Role, ClusterRole, RoleBinding).
- **Taints & Tolerations:** taint on node repels pods; toleration lets pod run there.
- **Node Affinity / nodeSelector:** attach pod to specific nodes.
- **Helm:** package manager for Kubernetes (charts). `helm install myapp ./chart`, `helm upgrade`, `helm rollback`, `helm list`.
- **Minikube / kind / kubeadm:** local / local-docker / production-style cluster setup tools. Managed: EKS, AKS, GKE.

## 7.7 Pod Troubleshooting (very common question!)
| Status | Meaning | Check |
|--------|---------|-------|
| `Pending` | Not scheduled | `describe pod` → insufficient resources / PVC / taints |
| `ImagePullBackOff` / `ErrImagePull` | Can't pull image | Wrong image name/tag, registry auth |
| `CrashLoopBackOff` | Container keeps crashing | `kubectl logs --previous`, wrong config/command |
| `OOMKilled` | Out of memory | Increase memory limit |
| `ContainerCreating` (stuck) | Volume/network issue | `describe pod` |
| `Running` but not working | App/service issue | check Service selector, readiness probe, endpoints (`kubectl get endpoints`) |

## 7.8 Interview Questions
1. **Pod vs Container?** → Pod wraps one or more containers sharing network & storage.
2. **Deployment vs StatefulSet?** → Deployment for stateless; StatefulSet for stateful with stable names/storage.
3. **ConfigMap vs Secret?** → ConfigMap plain config; Secret sensitive (base64, not encrypted by default).
4. **ClusterIP vs NodePort vs LoadBalancer?** → Internal / node port / cloud LB.
5. **Service vs Ingress?** → Service = L4 exposure; Ingress = L7 HTTP routing, host/path, TLS.
6. **How does a rolling update work?** → New pods created gradually, old removed after ready.
7. **How to rollback?** → `kubectl rollout undo deployment/name`.
8. **What is etcd?** → Cluster's database.
9. **What if a node goes down?** → Controller reschedules pods on other nodes.
10. **Liveness vs readiness?** → Liveness restarts; readiness controls traffic.
11. **What is HPA?** → Auto-scales pod count by CPU/memory/custom metrics.
12. **Namespace use?** → Isolate environments/teams; apply quotas.
13. **What is a DaemonSet?** → One pod per node.
14. **How do pods communicate?** → Every pod gets its own IP; flat network; Service DNS `svc.namespace.svc.cluster.local`.
15. **What is a sidecar container?** → Helper container in same pod (log shipper, proxy).
16. **Imperative vs Declarative?** → Imperative = `kubectl create`; Declarative = `kubectl apply -f` (preferred).
17. **What is kube-proxy?** → Handles service networking rules on each node.
18. **What is Helm?** → Package manager/templating for K8s manifests.

---

# 8. Terraform

## 8.1 What is Terraform?
Terraform (by HashiCorp) is an **Infrastructure as Code (IaC)** tool. You **describe** the infrastructure you want (servers, networks, databases) in `.tf` files, and Terraform **creates** it on AWS, Azure, GCP etc.
- **Declarative:** you say *what* you want, not *how*.
- **Cloud-agnostic:** same tool for many providers.

## 8.2 Core Concepts
| Term | Meaning |
|------|---------|
| **Provider** | Plugin to talk to a platform (aws, azurerm, google) |
| **Resource** | Infra object to create (EC2, S3, VPC) |
| **Data source** | Read existing info (e.g. latest AMI) |
| **Variable** | Input parameter |
| **Output** | Value printed after apply (e.g. public IP) |
| **Module** | Reusable group of resources |
| **State file** (`terraform.tfstate`) | Record of what Terraform created |
| **Backend** | Where state is stored (local, S3 + DynamoDB lock) |
| **Workspace** | Multiple environments with same code |
| **Provisioner** | Run scripts on resource (avoid if possible) |
| **locals** | Named expressions inside config |

## 8.3 Workflow
```
terraform init  →  terraform validate  →  terraform plan  →  terraform apply  →  terraform destroy
```

## 8.4 Commands by Category
| Command | Use |
|---------|-----|
| `terraform init` | Download providers/modules, setup backend |
| `terraform fmt` | Format code |
| `terraform validate` | Check syntax |
| `terraform plan` | Preview changes (dry run) |
| `terraform plan -out=tfplan` | Save plan |
| `terraform apply` | Create/update infra |
| `terraform apply -auto-approve` | Skip confirmation |
| `terraform destroy` | Delete everything |
| `terraform show` | Show state |
| `terraform output` | Show outputs |
| `terraform state list` | List resources in state |
| `terraform state rm <res>` | Remove from state (not from cloud) |
| `terraform import <res> <id>` | Bring existing resource under Terraform |
| `terraform taint` / `-replace=<res>` | Force recreate |
| `terraform workspace new dev` | Create workspace |
| `terraform apply -var="env=prod"` | Pass variable |
| `terraform refresh` | Sync state with real infra |

## 8.5 Example – Create an EC2 instance on AWS

**provider.tf**
```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
}

provider "aws" {
  region = "ap-south-1"
}
```

**variables.tf**
```hcl
variable "instance_type" {
  type    = string
  default = "t2.micro"
}
```

**main.tf**
```hcl
resource "aws_instance" "web" {
  ami           = "ami-0abcdef1234567890"
  instance_type = var.instance_type

  tags = {
    Name = "my-web-server"
  }
}

resource "aws_security_group" "web_sg" {
  name = "web-sg"
  ingress {
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }
}
```

**outputs.tf**
```hcl
output "public_ip" {
  value = aws_instance.web.public_ip
}
```

Run:
```bash
terraform init
terraform plan
terraform apply
terraform destroy   # clean up to avoid AWS bill!
```

## 8.6 Remote State (Team Work)
```hcl
terraform {
  backend "s3" {
    bucket         = "my-tf-state"
    key            = "prod/terraform.tfstate"
    region         = "ap-south-1"
    dynamodb_table = "tf-lock"      # prevents two people applying at once
    encrypt        = true
  }
}
```

## 8.7 Module Example
```hcl
module "vpc" {
  source     = "./modules/vpc"
  cidr_block = "10.0.0.0/16"
}
```

## 8.8 Useful Features
- **count / for_each:** create multiple resources
- **depends_on:** explicit dependency
- **lifecycle:** `prevent_destroy`, `create_before_destroy`, `ignore_changes`
- **`.terraform.lock.hcl`:** locks provider versions
- Always add `.terraform/` and `*.tfstate` to `.gitignore` (state can contain secrets!)

## 8.9 Interview Questions
1. **What is Terraform state? Why important?** → Maps your code to real resources; used to calculate changes.
2. **What if state file is lost/corrupted?** → Use remote state with versioning; recover or `terraform import` resources.
3. **`plan` vs `apply`?** → plan = preview; apply = execute.
4. **What is a module?** → Reusable package of Terraform code.
5. **Terraform vs Ansible?** → Terraform = provisioning infra (declarative); Ansible = configuring software on servers (procedural, agentless).
6. **Terraform vs CloudFormation?** → CloudFormation = AWS only; Terraform = multi-cloud.
7. **What is state locking?** → Prevents concurrent modifications (DynamoDB lock).
8. **`terraform import`?** → Adds an existing resource into state.
9. **How to manage multiple environments?** → Workspaces or separate folders/tfvars per environment.
10. **What is drift?** → Real infra differs from code (someone changed manually). Detect with `plan`.
11. **`count` vs `for_each`?** → count = index based; for_each = key based (safer).
12. **Is Terraform idempotent?** → Yes, applying again with no change does nothing.
13. **How do you keep secrets safe?** → Don't hardcode; use env vars, Vault, AWS Secrets Manager, mark `sensitive = true`.
14. **What is `terraform destroy`?** → Deletes all managed resources.

---

# 9. Ansible

## 9.1 What is Ansible?
Ansible is a **configuration management & automation** tool. It configures many servers at once (install packages, copy files, start services).
- **Agentless:** only needs **SSH** (no software on target servers)
- **Push-based**
- **YAML playbooks** (easy to read)
- **Idempotent:** running twice gives same result (won't reinstall if already installed)

## 9.2 Key Terms
| Term | Meaning |
|------|---------|
| **Control Node** | Machine where Ansible is installed |
| **Managed Nodes** | Servers being configured |
| **Inventory** | List of servers (`hosts` file) |
| **Playbook** | YAML file with tasks |
| **Play** | Set of tasks for a group of hosts |
| **Task** | Single action using a module |
| **Module** | Built-in tool (apt, copy, service, file, user) |
| **Role** | Reusable, structured playbook folder |
| **Handler** | Task run only when notified (e.g. restart service) |
| **Facts** | Auto-collected system info |
| **Vault** | Encrypt secrets |
| **Galaxy** | Community role repository |
| **Template (Jinja2)** | Dynamic config files `.j2` |

## 9.3 Inventory Example
```ini
[webservers]
web1 ansible_host=192.168.1.10
web2 ansible_host=192.168.1.11

[dbservers]
db1 ansible_host=192.168.1.20

[all:vars]
ansible_user=ubuntu
ansible_ssh_private_key_file=~/.ssh/key.pem
```

## 9.4 Ad-hoc Commands (quick one-liners)
```bash
ansible all -m ping                              # test connection
ansible webservers -m apt -a "name=nginx state=present" -b
ansible all -m shell -a "uptime"
ansible all -m copy -a "src=a.txt dest=/tmp/a.txt"
ansible all -m service -a "name=nginx state=restarted" -b
```
`-i` inventory, `-m` module, `-a` arguments, `-b` become sudo.

## 9.5 Playbook Example – Install & start nginx
```yaml
---
- name: Setup web server
  hosts: webservers
  become: yes

  vars:
    app_port: 80

  tasks:
    - name: Install nginx
      apt:
        name: nginx
        state: present
        update_cache: yes

    - name: Copy index page
      copy:
        src: index.html
        dest: /var/www/html/index.html
      notify: Restart nginx

    - name: Ensure nginx is running
      service:
        name: nginx
        state: started
        enabled: yes

  handlers:
    - name: Restart nginx
      service:
        name: nginx
        state: restarted
```
Run:
```bash
ansible-playbook -i inventory site.yml
ansible-playbook site.yml --check      # dry run
ansible-playbook site.yml --syntax-check
ansible-playbook site.yml -v           # verbose
ansible-playbook site.yml --tags web
```

## 9.6 Useful Features
```yaml
# Loop
- name: Install packages
  apt: name={{ item }} state=present
  loop: [git, curl, vim]

# Conditional
- name: Install on Ubuntu only
  apt: name=nginx state=present
  when: ansible_distribution == "Ubuntu"

# Register output
- shell: uptime
  register: result
- debug: var=result.stdout
```
**Role structure:** `ansible-galaxy init myrole` →
```
myrole/ tasks/ handlers/ templates/ files/ vars/ defaults/ meta/
```
**Vault:** `ansible-vault create secrets.yml`, `ansible-vault encrypt/decrypt/edit`, run with `--ask-vault-pass`.

## 9.7 Common Modules
`apt`, `yum`, `package`, `copy`, `template`, `file`, `service`/`systemd`, `user`, `group`, `command`, `shell`, `git`, `docker_container`, `lineinfile`, `cron`, `debug`, `uri`, `get_url`, `unarchive`.

## 9.8 Interview Questions
1. **Why agentless?** → Uses SSH; nothing to install/maintain on servers.
2. **What is idempotency?** → Same playbook repeated → same final state, no duplicate changes.
3. **Playbook vs Role?** → Playbook = file with tasks; Role = organized reusable structure.
4. **`command` vs `shell` module?** → shell supports pipes/redirects/env vars; command is safer.
5. **What are handlers?** → Run only if notified by a changed task (e.g. restart after config change).
6. **Ansible vs Terraform?** → Ansible configures software; Terraform provisions infrastructure.
7. **Ansible vs Puppet/Chef?** → Ansible agentless/YAML; others agent-based/DSL.
8. **How to protect secrets?** → Ansible Vault.
9. **What is inventory (static vs dynamic)?** → Static = file; Dynamic = fetched from cloud (AWS EC2 plugin).
10. **What are facts?** → System info gathered by `setup` module.
11. **How to run only on one host?** → `--limit web1`.
12. **What does `become: yes` do?** → Run with sudo/root.

---

# 10. Jenkins

## 10.1 What is Jenkins?
Jenkins is an **open-source automation server** used for **CI/CD**. It automatically **builds, tests and deploys** code when developers push changes. Written in Java, runs on port **8080**, has 1800+ plugins.

## 10.2 Key Terms
| Term | Meaning |
|------|---------|
| **Job / Project** | A task Jenkins runs |
| **Pipeline** | Job defined as code (stages) |
| **Jenkinsfile** | Text file with pipeline code (stored in Git) |
| **Master/Controller** | Main Jenkins server (schedules) |
| **Agent/Node/Slave** | Machine that actually runs builds |
| **Executor** | Slot to run a build on a node |
| **Workspace** | Folder where job runs |
| **Plugin** | Add-on features (Git, Docker, Slack…) |
| **Trigger** | What starts a build (webhook, poll SCM, cron, manual) |
| **Credentials** | Securely stored passwords/keys/tokens |
| **Artifact** | Output of build (jar, zip) |
| **Build Parameters** | Inputs when starting build |

## 10.3 Job Types
- **Freestyle** – simple, GUI configured
- **Pipeline** – Jenkinsfile (recommended)
- **Multibranch Pipeline** – auto pipeline for each Git branch
- Maven, folder, etc.

## 10.4 Installation (Ubuntu quick)
```bash
sudo apt update
sudo apt install openjdk-17-jdk -y
# add Jenkins repo, then
sudo apt install jenkins -y
sudo systemctl enable --now jenkins
sudo cat /var/lib/jenkins/secrets/initialAdminPassword   # first login password
# open http://<server-ip>:8080
```
Home dir: `/var/lib/jenkins`. Logs: `/var/log/jenkins/jenkins.log`.

## 10.5 Declarative Jenkinsfile Example
```groovy
pipeline {
    agent any

    environment {
        IMAGE = "nasir/myapp"
        TAG   = "${BUILD_NUMBER}"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/nasir/myapp.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test'
            }
        }
        stage('Docker Build & Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub',
                                 usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh '''
                      docker build -t $IMAGE:$TAG .
                      echo $PASS | docker login -u $USER --password-stdin
                      docker push $IMAGE:$TAG
                    '''
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'kubectl set image deployment/myapp myapp=$IMAGE:$TAG'
            }
        }
    }

    post {
        success { echo 'Pipeline succeeded ✅' }
        failure { echo 'Pipeline failed ❌' }
        always  { cleanWs() }
    }
}
```

**Declarative vs Scripted:** Declarative = structured `pipeline { }` (easier, recommended). Scripted = `node { }` Groovy (more flexible).

## 10.6 Useful Concepts
- **Webhook trigger:** GitHub notifies Jenkins on push (better than polling).
- **Poll SCM:** Jenkins checks Git periodically (`H/5 * * * *`).
- **Parallel stages:** `parallel { stage('A'){...} stage('B'){...} }`
- **`when` condition:** run stage only on branch `main`.
- **Input step:** manual approval before deploy.
- **Shared libraries:** reusable pipeline code.
- **Backup:** copy `/var/lib/jenkins`.
- **Security:** enable auth, RBAC/Matrix, use Credentials plugin, never hardcode secrets.

## 10.7 Interview Questions
1. **What is Jenkins & why use it?** → CI/CD automation server; automates build/test/deploy.
2. **Freestyle vs Pipeline?** → Freestyle = GUI; Pipeline = code (Jenkinsfile), version controlled.
3. **What is Jenkinsfile?** → Pipeline definition stored in repo.
4. **Declarative vs Scripted?** → See 10.5.
5. **What is an agent?** → Worker node running builds (distributed builds).
6. **How to trigger a build automatically?** → Webhook, Poll SCM, schedule.
7. **How to store credentials?** → Jenkins Credentials store, use `withCredentials`.
8. **How to secure Jenkins?** → Auth, RBAC, plugins updated, HTTPS, no secrets in code.
9. **Build failed — what do you do?** → Check Console Output, workspace, fix, rebuild.
10. **What is a multibranch pipeline?** → Automatically creates pipeline per branch with a Jenkinsfile.
11. **How to run Jenkins in Docker?** → `docker run -p 8080:8080 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts`.
12. **Jenkins vs GitHub Actions?** → Jenkins self-hosted/flexible/plugins; GitHub Actions hosted/YAML/integrated with GitHub.

---

# 11. GitHub Actions

## 11.1 What is it?
CI/CD built into GitHub. Workflows are YAML files in `.github/workflows/`.

| Term | Meaning |
|------|---------|
| **Workflow** | Automated process (YAML file) |
| **Event/Trigger** | `push`, `pull_request`, `schedule`, `workflow_dispatch` |
| **Job** | Group of steps on one runner |
| **Step** | Single command or action |
| **Action** | Reusable step (`actions/checkout@v4`) |
| **Runner** | Machine running job (`ubuntu-latest`, self-hosted) |
| **Secrets** | Encrypted variables (`${{ secrets.NAME }}`) |

## 11.2 Example – Build & push Docker image
```yaml
name: CI

on:
  push:
    branches: [ main ]
  pull_request:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - run: npm ci
      - run: npm test

      - name: Login to Docker Hub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKER_USER }}
          password: ${{ secrets.DOCKER_PASS }}

      - name: Build & push
        uses: docker/build-push-action@v5
        with:
          push: true
          tags: nasir/myapp:${{ github.sha }}
```
**Interview:** *Jobs run in parallel by default; use `needs:` to make order.* *Matrix strategy* runs same job on multiple versions/OS.

---

# 12. ArgoCD & GitOps

## 12.1 What is GitOps?
**Git = single source of truth** for what should run in production. Any change is made via **Git commit / Pull Request**, and a tool automatically makes the cluster match Git.

Benefits: audit trail (git history), easy rollback (`git revert`), consistency, security (no direct kubectl access).

## 12.2 What is ArgoCD?
ArgoCD is a **declarative GitOps Continuous Delivery tool for Kubernetes**. It continuously compares **desired state (Git)** with **live state (cluster)** and syncs them.

```
Developer → Git repo (manifests/Helm) ← ArgoCD watches → Kubernetes cluster
```
**CI (Jenkins/GH Actions)** builds image and updates the image tag in Git → **ArgoCD (CD)** deploys it.

## 12.3 Key Terms
| Term | Meaning |
|------|---------|
| **Application** | ArgoCD resource: Git repo path ↔ cluster/namespace |
| **Project (AppProject)** | Group apps; restrict repos/clusters |
| **Sync** | Make cluster match Git |
| **Sync Status** | `Synced` / `OutOfSync` |
| **Health Status** | `Healthy`, `Progressing`, `Degraded`, `Missing` |
| **Auto-sync** | Sync automatically on Git change |
| **Self-heal** | Revert manual changes in cluster |
| **Prune** | Delete resources removed from Git |
| **Drift** | Cluster ≠ Git |
| **App of Apps** | One app that manages many apps |
| **ApplicationSet** | Generate many apps from a template |
| **Rollback** | Go to previous synced revision |

## 12.4 Install & Access
```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# get admin password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

# access UI
kubectl port-forward svc/argocd-server -n argocd 8080:443
# open https://localhost:8080  (user: admin)
```

## 12.5 CLI Commands
```bash
argocd login localhost:8080
argocd app list
argocd app get myapp
argocd app sync myapp
argocd app history myapp
argocd app rollback myapp <ID>
argocd app delete myapp
argocd repo add https://github.com/user/repo.git
argocd cluster list
```

## 12.6 Application YAML Example
```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: myapp
  namespace: argocd
spec:
  project: default
  source:
    repoURL: https://github.com/nasir/k8s-manifests.git
    targetRevision: main
    path: myapp
  destination:
    server: https://kubernetes.default.svc
    namespace: production
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
    syncOptions:
      - CreateNamespace=true
```

## 12.7 Interview Questions
1. **What is GitOps?** → Using Git as source of truth, with automated sync to infra.
2. **Push vs Pull deployment?** → Push (Jenkins runs kubectl); Pull (ArgoCD inside cluster pulls from Git — more secure).
3. **What is OutOfSync?** → Live state differs from Git.
4. **Self-heal?** → Reverts manual changes to match Git.
5. **How to rollback in ArgoCD?** → `git revert` (best) or `argocd app rollback`.
6. **ArgoCD vs Jenkins?** → Jenkins = CI (build/test); ArgoCD = CD (deploy to K8s).
7. **ArgoCD vs Flux?** → Both GitOps tools; ArgoCD has a UI.
8. **Where are secrets stored?** → Not in Git plain; use Sealed Secrets, External Secrets, Vault.
9. **What is App of Apps?** → Pattern where one parent app deploys many child apps.
10. **Which manifests supported?** → Plain YAML, Helm, Kustomize, Jsonnet.

---

# 13. Monitoring (Prometheus & Grafana)

## 13.1 Why Monitoring?
Detect problems before users do, track performance, plan capacity, get alerts.

**3 Pillars of Observability:** **Metrics** (numbers – Prometheus), **Logs** (events – ELK/Loki), **Traces** (request path – Jaeger).

## 13.2 Prometheus
Open-source **metrics monitoring + alerting** system. **Pull-based** (scrapes `/metrics` endpoints). Stores **time-series** data. Query language: **PromQL**. Port **9090**.

| Component | Role |
|-----------|------|
| **Prometheus Server** | Scrapes & stores metrics |
| **Exporters** | Expose metrics (node_exporter for Linux – port 9100) |
| **Alertmanager** | Sends alerts (email, Slack) |
| **Pushgateway** | For short-lived jobs |
| **Service Discovery** | Auto-find targets (Kubernetes) |

**prometheus.yml**
```yaml
global:
  scrape_interval: 15s
scrape_configs:
  - job_name: 'node'
    static_configs:
      - targets: ['localhost:9100']
```
**PromQL examples**
```
up                                              # is target up (1/0)
node_memory_MemAvailable_bytes
rate(http_requests_total[5m])                   # requests per second
100 - (avg(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)   # CPU %
```
**Metric types:** Counter (only goes up), Gauge (up/down), Histogram, Summary.

## 13.3 Grafana
Visualization tool: dashboards/graphs using data from Prometheus, Loki, etc. Port **3000** (default admin/admin). Supports alerts.

## 13.4 Interview Questions
1. **Prometheus pull vs push?** → Prometheus pulls from targets.
2. **What is an exporter?** → Converts system metrics into Prometheus format.
3. **Prometheus vs Grafana?** → Prometheus collects/stores; Grafana visualizes.
4. **What is PromQL?** → Prometheus query language.
5. **What is Alertmanager?** → Handles alert routing, grouping, silencing.
6. **Counter vs Gauge?** → Counter only increases; gauge goes up and down.
7. **What is ELK?** → Elasticsearch + Logstash + Kibana for log management.

---

# 14. AWS / Cloud Basics

## 14.1 Cloud Models
- **IaaS** (EC2 – you manage OS), **PaaS** (Elastic Beanstalk – you manage code), **SaaS** (Gmail)
- **Public / Private / Hybrid** cloud
- **Shared responsibility:** AWS secures the cloud; you secure what's *in* the cloud.

## 14.2 Core Services
| Category | Service | Use |
|----------|---------|-----|
| Compute | **EC2** | Virtual servers |
| | **Lambda** | Serverless functions |
| | **ECS / EKS** | Containers / Kubernetes |
| Storage | **S3** | Object storage |
| | **EBS** | Disk for EC2 |
| | **EFS** | Shared file system |
| Network | **VPC** | Private network |
| | **Subnet** | Public/private segments |
| | **Internet Gateway** | Internet access |
| | **NAT Gateway** | Private subnet → internet |
| | **Route 53** | DNS |
| | **ELB** | Load balancer |
| | **Security Group** | Instance firewall (stateful) |
| | **NACL** | Subnet firewall (stateless) |
| Database | **RDS** | Managed SQL |
| | **DynamoDB** | NoSQL |
| Security | **IAM** | Users, roles, policies |
| Monitoring | **CloudWatch** | Metrics/logs/alarms |
| | **CloudTrail** | API audit logs |
| DevOps | **CodePipeline, CodeBuild, ECR** | CI/CD, image registry |
| Scaling | **Auto Scaling Group** | Add/remove EC2 automatically |

## 14.3 Important Concepts
- **Region / Availability Zone:** Region = geographic area; AZ = isolated data centers inside a region.
- **IAM Role vs User:** User = long-term identity; Role = temporary permissions assumed by services.
- **Principle of least privilege:** Give only required permissions.
- **Security Group vs NACL:** SG = instance level, stateful, allow-only; NACL = subnet level, stateless, allow+deny.
- **Public vs Private subnet:** Public has route to Internet Gateway.
- **S3 storage classes:** Standard, IA, Glacier.
- **EC2 pricing:** On-Demand, Reserved, Spot.

## 14.4 AWS CLI
```bash
aws configure
aws s3 ls
aws s3 cp file.txt s3://bucket/
aws ec2 describe-instances
aws ec2 start-instances --instance-ids i-123
aws iam list-users
```

---

# 15. Common Interview Questions (Rapid Fire)

### Scenario Based
1. **Website is down — how do you troubleshoot?**
   → Check DNS → server reachable (`ping`) → port open (`ss`, `curl`) → service status (`systemctl status`) → logs → disk/CPU/memory → recent deployments (rollback) → LB health checks.
2. **Deployment failed in production?** → Rollback quickly (`kubectl rollout undo` / revert Git commit), check logs, fix, redeploy via pipeline.
3. **Pod in CrashLoopBackOff?** → `kubectl logs --previous`, `describe pod`, check config/env/command/resources.
4. **Server disk is full?** → `df -h`, `du -sh /*`, clear logs (`logrotate`), old docker images (`docker system prune`).
5. **How do you secure a CI/CD pipeline?** → Secrets in vault/credentials store, least privilege, scan images (Trivy), scan code (SonarQube), signed commits, approvals.
6. **How to achieve zero-downtime deployment?** → Rolling update, blue-green, canary, readiness probes.
7. **Explain a project you built.** → Use format: *Problem → Tools used → What you did → Result.*

### Deployment Strategies
| Strategy | Meaning |
|----------|---------|
| **Rolling** | Replace instances gradually |
| **Blue-Green** | Two identical environments; switch traffic at once |
| **Canary** | Release to small % users first |
| **Recreate** | Stop old, start new (downtime) |

### Quick Definitions
- **Idempotency:** same operation many times → same result.
- **Immutable infrastructure:** never modify servers; replace them.
- **Scalability:** Vertical (bigger machine) vs Horizontal (more machines).
- **High Availability:** system stays up despite failures.
- **SLA / SLO / SLI:** Agreement / Objective / Indicator of service reliability.
- **MTTR / MTBF:** Mean time to recover / between failures.
- **DevSecOps:** Security added into DevOps pipeline (Trivy, SonarQube, Snyk).
- **Microservices vs Monolith:** many small independent services vs one big app.
- **Infrastructure drift, Technical debt, Rollback, Hotfix, Artifact, Registry, Webhook.**
- **Trivy:** container vulnerability scanner. **SonarQube:** code quality scanner. **Nexus/JFrog:** artifact repository. **Vault:** secrets management.

### HR / Internship Questions
- Tell me about yourself. (Short: background → DevOps learning → projects → goal)
- Why DevOps? Why this company?
- What tools have you used hands-on? (Be honest, mention projects)
- What do you do when you don't know something? (Google/docs/ask, learn fast)
- Where do you see yourself in 3 years?

> 💡 **Tip:** Interviewer *concept + practical* dekhta hai. Hamesha example do: "I used Docker to containerize my app and deployed it on Kubernetes using ArgoCD."

---

# 16. Daily Revision Plan

| Day | Topic |
|-----|-------|
| 1 | DevOps basics + Linux commands |
| 2 | Linux permissions, processes, networking, cron |
| 3 | Bash scripting (write 3 scripts) |
| 4 | Git (practice branch, merge conflict, rebase) |
| 5 | Docker basics + Dockerfile |
| 6 | Docker Compose + volumes + networks |
| 7 | 🔁 **Revision** Day 1–6 |
| 8 | Kubernetes architecture + objects |
| 9 | kubectl + YAML (Deployment, Service, Ingress) |
| 10 | K8s troubleshooting, Helm, probes |
| 11 | Terraform basics + AWS EC2 practice |
| 12 | Terraform state, modules, backend |
| 13 | Ansible inventory + playbooks + roles |
| 14 | 🔁 **Revision** Day 8–13 |
| 15 | Jenkins pipeline (Jenkinsfile) |
| 16 | GitHub Actions |
| 17 | ArgoCD + GitOps |
| 18 | Prometheus + Grafana |
| 19 | AWS basics (IAM, VPC, EC2, S3) |
| 20 | Scenario-based questions |
| 21 | 🔁 **Full Revision + Mock Interview** |

### Rules for revision
1. Roz **command khud type karo** — sirf parhna kaafi nahi.
2. Har topic ke baad **3 questions apne aap ko bolo** (speaking practice).
3. Ek **mini project** banao: *GitHub → Jenkins/Actions → Docker → Kubernetes → ArgoCD → Prometheus*.
4. Weak topics ko ⭐ mark karo aur dobara parho.

---

⭐ **If this helped, star the repo and keep learning!** Happy DevOps journey 🚀
