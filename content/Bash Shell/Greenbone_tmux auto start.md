---
title: 🐱‍💻 OxMdk
---

### Greenbone & Tmux autostart Example:
```sh
#!/bin/sh
sudo mkdir /run/gvm/ && sudo chown mdk -R /run/gvm/

tmux new -d -s GreenBone "cd /home/mdk/APPS/ospd-scanner/ ; redis-server redis-openvas.conf ; read" \; \
split-window -d "cd /home/mdk/APPS/ospd-scanner/ ; source ./bin/activate ; sudo ln -s /home/mdk/APPS/Greebone-11-16-21/run/redis/redis.sock /run/redis/ ; ./bin/ospd-openvas -s ospd.conf -f --lock-file-dir=/home/mdk/APPS/Greebone-11-16-21/run/ospd/ ; read" \; \
new-window -d "gvmd -f ; read" \; next-window \; split-window -d "sudo gsad -f --munix-socket=/run/gvm/gvmd.sock ; read"
```
