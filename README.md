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

pkg install /var/cache/pkg/*
```
