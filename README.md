# Offline-PfSense-pkg-Install
Offline install instructions for package install

## On the ONLINE PFsense
## Must be same version as offline firewall

```
rm -f /var/cache/pkg/*

pkg fetch suricata
pkg fetch -d suricata
pkg fetch pfsense-pkg-suricata
OR
Create zip file for SCP
```

## On OFFLINE Pfsense:
```
ssh user@pfesnse 'rm -f /var/cache/pkg/*'

scp /var/cache/pkg/* user@pfesnse:/var/cache/pkg/
OR
SCP zip file and extract

ssh user@pfesnse

pkg install -f -l /var/cache/pkg/*
```

# Offline PFSense Suricata ETOpen Rull install

## Download rules and MD5 signature from:

### https://rules.emergingthreats.net/open/suricata-5.0/

---
### example:

### https://rules.emergingthreats.net/open/suricata-5.0/emerging-all.rules.tar.gz
### https://rules.emergingthreats.net/open/suricata-5.0/emerging-all.rules.tar.gz.md5
---

## In directory where files are located:
`
python3 -m http.server
`
Browse to ensure it works: http://<xx.xx.xx.xx>:8000/
![screenshot](/images/PfSense_et_open_pytnohttp.PNG)

## On PfSense

#### select Services --> Suricata --> Global Settings

#### Check ETOpen and Use Custom URL

#### In the ETOpen Custom Rule Download URL type in: http://<xx.xx.xx.xx>:8000/emerging-all.rules.tar.gz

#### Select Services --> Suricata --> Updates
![screenshot](/images/PfSense_et_open.PNG)

#### Select --> Update

![screenshot](/images/PfSense_et_open_success.PNG)
