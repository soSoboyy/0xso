---
{"dg-publish":true,"permalink":"/htb/cjca/recon-tools/","dg-note-properties":{}}
---

#### recon-ng
#recon-ng
```bash
# Check for available options
info
# Load a module
modules load 

#Launch a reco task
options set SOURCE "whatever"

# There is also the option to unset sources, ports, etc.
options unset port 80
options unset SOURCE

#Run task
run
```

==Search for web presence based on the username:==
```bash

modules load profiler
db insert profile
"username"
run
show profiles
```

#### Nmap
enumerate the open ports in a target:
`nmap <target IP>`

