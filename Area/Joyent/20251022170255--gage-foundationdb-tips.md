---
id: 20251022170255--gage-foundationdb-tips
aliases:
  - Gage FoundationDB tips
tags:
  - area
  - joyent
area:
  - joyent
date: Wednesday October 22nd 2025
---
# Gage FoundationDB tips

## Gage FoundationDB tips Notes

```bash
for i in {17..24}; do
  echo "Cluster $i:"
  fdbcli -C cluster_${i}/fdb.cluster --exec "coordinators" | grep {IPADDRESS}
done
```
