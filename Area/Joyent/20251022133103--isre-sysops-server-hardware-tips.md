---
id: 20251022133103--isre-sysops-server-hardware-tips
aliases:
  - ISRE Sysops Server Hardware Tips
tags:
  - area
  - joyent
area:
  - joyent
date: Wednesday October 22nd 2025
---

# ISRE  Server Hardware Tips  

## Generate Product code on BOM for Supermicro

[[id:71dc318e-0f52-49c1-9203-65e59eee9575][Jon Burgoyne]] Sent this over   2025 03 17
```bash
jon@fdsa:~/joyent$ cat smci_activate.sh
#!/bin/bash

echo -n "${1}" | xxd -r -p | \
  openssl dgst -sha1 -mac HMAC -macopt hexkey:8544E3B47ECA58F9583043F8 | \
  awk '{print $2}' | sed 's/.\{4\}/&-/g' | cut -c 1-29
```


## Links

+ [Foundation DB Host Maintenance](https://wiki-joyent.atlassian.net/wiki/spaces/GAGE/pages/25662920/Host+Maintenance+-+Gateway+FoundationDB])
+ [Smaug Host Maintenance](https://wiki-joyent.atlassian.net/wiki/spaces/GAGE/pages/25661940/Host+Maintenance+-+Smaug+Shrimp)
+ [Proxmox VM Notes](id:0f021c3e-1216-4522-9688-d48561638793)
+ [Gage Jenkins](https://gage-jenkins.ap-northeast-1.samsungspc.com/)

