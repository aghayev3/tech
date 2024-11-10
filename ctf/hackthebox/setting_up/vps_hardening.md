# VPS Hardening

Another necessary step in our configuration and setup of our VPS is the hardening of the system and access. We should limit our access to the VPS to SSH and disable all other services on the VPS. Finally, we will reduce the attack vectors to a minimum and provide only one possible access to our VPS, which we will secure in the best possible way. We should keep in mind that, if possible, we should not store any sensitive data on the VPS, or at least only for a short period when we perform an internal penetration test. In doing so, we should follow the principle that someone could gain access to the system sooner or later.

However, since in this case, the VPS is only used as a source for our organization and tools and we can access these resources via SSH, we should secure and harden the SSH server accordingly so that no one else (or at least no one other than the team members) can access it. There are many ways to harden it, and this includes the following precautions, but not limited to:


- Install Fail2ban
- Working only with SSH keys
- Reduce Idle timeout interval
- Disable passwords
- Disable x11 forwarding
- Use a different port
- Limit users' SSH access
- Disable root logins
- Use SSH proto 2
- Enable 2FA Authentication for SSH


It is highly recommended to try these settings and precautions first in a local VM we have created before making these settings on a VPS.

One of the first steps in hardening our system is updating and bringing the system up-to-date. We can do this with the following commands:

### Update the System

```
[cry0l1t3@VPS ~]$ sudo apt update -y && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt autoclean -y
```

## SSH Hardening

SSH is always installed on the VPS










