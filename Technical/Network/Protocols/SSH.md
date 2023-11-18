---
tag: Network
---

# How to ssh to server

1. **How to ssh to server manually**

Host: 13.212.131.68

User: ubuntu

```bash
$ ssh ubuntu@13.212.131.68 -i Downloads/hodford-dev2.pem
```

1. **Add to config file in .ssh folder**

Host renyoo-bastion-uat

HostName 46.137.238.204

User ubuntu

IdentityFile ~/.ssh/renyoo-uat.pem

UserKnownHostsFile=/dev/nul

```bash
$ ssh renyoo-bastion-uat
```

# How to copy file to server

scp -i <location-to-private-key-file> <location-to-copying-file> <username@ip>:<location-to-copy-file>

Command: 

```bash
$ ssh -i Downloads/private-key.pem Downloads/test.text ubuntu@13.212.131.68:/home/ec2-user
```