# Install-MikroTik-CHR-on-VPS
Easy way for install Mikrotik’s Cloud Hosted Router on any Cloud VM

## Prerequisites

```bash
  1:
  VPS with VNC access (Preferably Debian 12)
  2:
  This network information is required:
  IP Address - Net Mask - IP Gateway
  3:
  In some cases you need to disable the Virtio driver!
```

## Find information manually
Find storage name
```bash
lsblk | grep disk | cut -d ' ' -f 1 | head -n 1
```
Find ethernet name
```bash
ip route show default | sed -n 's/.* dev \([^\ ]*\) .*/\1/p'
```
find ip address name
```bash
ip addr show $ETH | grep global | cut -d' ' -f 6 | head -n 1
```
find gateway name
```bash
ip route list | grep default | cut -d' ' -f 3
```
## Installation

For MikroTik 7.17 Classic (untested, supposed working)

```bash
  bash -c "$(curl -L https://raw.githubusercontent.com/Friezer-85/Install-MikroTik-CHR-on-VPS/main/install.sh)"
```

For MikroTik 6.49.17 Elseif Version (tested, working)

```bash
  bash -c "$(curl -L https://raw.githubusercontent.com/Friezer-85/Install-MikroTik-CHR-on-VPS/main/elseif649.sh)"
```

For MikroTik 7.17 Elseif Version (untested)

```bash
  bash -c "$(curl -L https://raw.githubusercontent.com/Friezer-85/Install-MikroTik-CHR-on-VPS/main/elseif.sh)"
```

After install be sure to turn off the server and turn on again
## Post installation settings

In some cases it is possible that the network settings inside the MikroTik may not be done correctly that you must manually and through the VNC console.
