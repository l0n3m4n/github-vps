<h1 align="center">
  Github-VPS
</h1>
<p align="center">
    <a href="https://visitorbadge.io/status?path=https%3A%2F%2Fgithub.com%2Fl0n3m4n%2Fgithub-vps">
    <img src="https://api.visitorbadge.io/api/visitors?path=https%3A%2F%2Fgithub.com%2Fl0n3m4n%2Fgithub-vps&label=Visitors&countColor=%2337d67a"/>
  </a>
    <a href="https://www.facebook.com/l0n3m4n">
        <img src="https://img.shields.io/badge/Facebook-%231877F2.svg?style=for-the-badge&logo=Facebook&logoColor=white" alt="Facebook">
    </a>
      <a href="https://www.twitter.com/l0n3m4n">
        <img src="https://img.shields.io/badge/Twitter-%23000000.svg?style=for-the-badge&logo=X&logoColor=white" alt="X">
    </a>
    <a href="https://medium.com/@l0n3m4n">
        <img src="https://img.shields.io/badge/Medium-12100E?style=for-the-badge&logo=medium&logoColor=white" alt="Medium">
    </a>
    <a href="https://www.python.org/">
    <img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54" alt="Python">
    </a>
    <a href="https://www.kali.org/">
    <img src="https://img.shields.io/badge/Kali-268BEE?style=for-the-badge&logo=kalilinux&logoColor=white" alt="Kali">      
    </a>
</p>
<br>
<br>

![neofetch](assets/neofetch.png)

## 📜 Description 
GitHub Codespaces allows developers and hackers to create and utilize their coding environments directly from GitHub in the cloud. As a CTF player or pentester, you can also leverage GitHub Codespaces similarly to a VPS (Virtual Private Server). This makes it easy to work on projects from anywhere with the flexibility of a portable development setup using Docker.

## 📚 Table of Contents
- 📜 [Description](#-description)
- 🔥 [What's Nice](#whats-nice)
- 🐳 [Docker Installation](#-docker-installation)
- 🙍🏻‍♂️ [Configuration](#-configuration)
- 🚫 [Temporarily Disabled](#-temporarily-disabled)
- 👨🏾‍⚖️ [License](#-license)

 
## 🔥 What's Nice
- Offers more power with `2-vCPUs`, `8GB-RAM`, and a temporary `32GB-SSD` storage drive.
- Higher performance with `4-vCPUs`, `16GB-RAM`, and a temporary `32GB-SSD` storage drive.
![machine_type](assets/machine_type.png)

### 🐳 Docker Installation

> [!NOTE] 
> Github codespace terminal
---
![starting](assets/starting.png)
```bash
# pulling images 
$ docker pull docker.io/kalilinux/kali-rolling

# Option 1: Priviliged mode (recommended for ctf players)
$ docker run --privileged -it kalilinux/kali-rolling /bin/bash

# Option 2: Interactive mode
$ docker run --tty --interactive kalilinux/kali-rolling
 
$ apt update && apt install -y kali-linux-default

$ apt update && apt install -y install kali-linux-headless
```
### Installation without errors
> [!TIP]
> Refer to default [installation Guide](./assets/installation_guide/readme.md)  


## Configuration
### Starting Docker Kali Image
```bash
# Display
$ docker ps -a

# Rename 
$ docker rename <current_name> <new_name>

# Status details 
$ docker inspect <container id>

# Start 
$ docker start <container id> (e.q) d36922fa21e8

# Attach 
$ docker attach <container id>

# Stop  
$ docker stop <container id>

# Remove
$ docker rm <container id>
```

### Adding non-root user 
![non-root](assets/add_non-root_user.png)
```bash
$ sudo apt update && sudo apt upgrade -y

# option 1:
$ adduser l0n3m4n

# option 2:
$ useradd -m -s /bin/bash l0n3m4n

# option 1: replace to your username
l0n3m4n ALL=(ALL:ALL) ALL

# option 2: 
$  echo "l0n3m4n ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers/l0n3m4n

# switching to non-root user
$ su - l0n3m4n

# verify
$ whoami
```

### Diskspace Monitoring 
```bash
# view ram details
$ free

# view disk space 'du'
$ du -h --max-depth=1 /

# view disk space GB
$ df -h

```

### Docker Privileged
> [!IMPORTANT]
> The way to use openvpn or enable `tun0` you need to add `--privileged` option instead using `--tty` by default, Docker containers do not have access to TUN/TAP devices on the host system due to security and isolation concerns.
```bash
# options 1:
$ docker run --privileged -it kalilinux/kali-rolling /bin/bash

# Option 2: Use --device Flag (More Secure)
# A more secure approach is to use the --device flag to explicitly map the TUN/TAP device from the host into the container. This approach is more controlled and limits access to only the necessary device.

$ docker run --device=/dev/net/tun:/dev/net/tun -it kalilinux/kali-rolling /bin/bash

# Verify TUN/TAP Functionality Inside the Container
$ ls -l /dev/net/tun
```

### New Terminal Session
> [!NOTE]
> Github codespace terminal
```bash
$ docker exec -it <container_id> /bin/bash
```

## 🚫 Temporarily Disabled 
If you've used 100% of the included services for GitHub Codespaces storage, a few things might happen depending on your account settings and actions.

1. **Inability to Use Codespaces**: You won't be able to create or use GitHub Codespaces until either your `free allotment resets next month` or you take action to manage your usage.
2. **Options to Regain Access**:
    - Set Up a Spending Limit: You can set up a `spending limit` on your GitHub account to prevent unexpected charges and manage your usage effectively.
    - Delete Unused Resources: Consider `deleting Codespaces` or `prebuilds` that are no longer needed to free up space and potentially reduce future charges.
3. **Access to In-Progress Work**: It's important to `export` any unpushed work to a branch if you want to retain access to your in-progress projects. This ensures you have a backup and can continue working on them when you regain access to Codespaces.
4. **Review Usage and Charges**: GitHub provides a `usage report` where you can see detailed information about your Codespaces and prebuild usage. This can help you understand your usage patterns and manage future usage effectively.
---
![codespace](assets/codespace.png)
![billing](assets/billing.png)

## 🔄 Changelog
### v1.1.0 - [2024-06-29]
- Adjustment:
    - Adding `privileged` user mode to enable TUN error when starting the OpenVPN file.
      
## 📝 Todo
- [ ] **Adding remotehost for graphical user inferface (GUI), this includes xrdp, ssh, noVNC and etc.**
- [ ] **Adding Automated builds Dockerfile to ensure consistency and reliability.**
- [ ] **Adding ngrok to exposed your cloud servers behind NATs and firewalls to the public internet over secure tunnels.**
- [ ] **Adding Openvpn default configuration to ensure privacy and security**

## 👨🏾‍⚖️ License
This project is under terms of the [MIT License](LICENSE). For fixing Bugs, create [issue](https://github.com/l0n3m4n/github-vps/issues/new)
