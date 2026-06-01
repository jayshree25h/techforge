# Linux Basics

This file will cover fundamental Linux commands commonly used by developers and DevOps engineers.

## Basic Commands
- **Navigation & files:** `ls -la` — list files; `cd /path` — change directory; `pwd` — print working directory
- **File ops:** `cp src dst`, `mv src dst`, `rm -rf path`, `mkdir -p dir`, `touch file`
- **View files:** `cat file`, `less file`, `head -n 50 file`, `tail -f logfile`
- **Disk & memory:** `df -h` — disk usage; `du -sh dir` — directory size; `free -m` — memory
- **Processes:** `ps aux | grep name`, `top` / `htop` (interactive)
- **System info:** `uname -a`, `whoami`, `uptime`, `hostname`

The is the Intermediate ~~CMD~~

## ~~Intermediate~~ Commands (scripting & ~~troubleshooting~~)
- **Search & text processing:** `grep -R "pattern" .`, `awk '{print $1}' file`, `sed -n '1,20p' file`
- ~~**Find & act:** `find / -type f -name '*.log' -mtime -7 -print`, `find . -exec rm {} \;` (use carefully)~~
- **Pipelines:** `command | tee out.txt | grep ERROR | wc -l`
- **Parallel/xargs:** `find . -name '*.py' | xargs -P4 -I{} pylint {}`
- **Networking basics:** `ip addr show`, `ss -tulwn` (open sockets), `curl -fsSL http://example.com` (HTTP checks)
- **Logs & services:** `systemctl status nginx`, `journalctl -u nginx -f` — follow service logs
- **Archive & sync:** `tar -czf backup.tgz /path`, `rsync -avz /src/ user@host:/dst/`
- **Permissions & users:** `chmod 640 file`, `chown user:group file`, `useradd -m alice`, `usermod -aG docker alice`
- **Scheduling:** `crontab -e` to edit cron jobs; `systemd-run --on-active=10s --unit=one-off /bin/echo hi`
- **JSON tooling:** `jq` for parsing JSON: `curl -s api | jq '.items[] | {name: .metadata.name}'`

## Advanced / DevOps-Focused Commands
- **Container tooling:** `docker ps`, `docker run -d --name app -p 8080:80 image`, `docker logs -f app`, `docker exec -it app /bin/bash`
- **Compose & Podman:** `docker-compose up -d`, `podman ps` (rootless containers)
- **Kubernetes:** `kubectl get pods -A`, `kubectl describe pod mypod`, `kubectl logs -f deploy/myapp`, `kubectl exec -it pod -- /bin/sh`, `kubectl port-forward svc/myapp 8080:80`
- **Helm:** `helm repo add stable https://charts.helm.sh/stable`, `helm upgrade --install release chart/ -f values.yaml`
- **Infrastructure CLIs:** `terraform init`, `terraform plan -out=plan.tfplan`, `terraform apply plan.tfplan`; `ansible-playbook site.yml -i inventory`
- **Network capture & diagnostics:** `tcpdump -i eth0 -nn -s0 -w capture.pcap`, `tshark -r capture.pcap`
- **DNS & network tools:** `dig +short example.com`, `nslookup`, `traceroute example.com`, `iperf3 -s / -c host` for throughput
- **Firewalls & security:** `iptables -L -n` or `nft list ruleset`, `getenforce` / `setenforce 0` (SELinux)
- **System tracing & perf:** `strace -f -o trace.log command`, `perf top`, `perf record -a -g -- sleep 10 && perf report`
- **Binary & port management:** `lsof -i :8080`, `ss -plnt | grep 8080`
- **Automation & CI helpers:** `git rev-parse --abbrev-ref HEAD`, `git log --oneline -n 5`, `ssh -i ~/.ssh/id_rsa user@host`, `scp -r build/ user@host:/opt/`

This is Short
## Short examples & tips
- Check HTTP endpoint availability: `curl -fsS -o /dev/null -w "%{http_code}\n" http://localhost:8080`
- Follow logs across a fleet (example): `ssh host1 'journalctl -u service -f' | grep ERROR`
- Safe copy with progress: `rsync -avh --progress /data/ backup:/data/`
- Quickly find large files: `du -ahx / | sort -rh | head -n 20`

---

Keep this file as a quick reference. Want me to ~~add~~ examples for a specific tool (Docker, kubectl, Terraform, Ansible)?
