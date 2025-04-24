> This information describes the migration process from CentOS 8 to Rocky Linux.
> The process is not as difficult as I thought before.
> 
## What is CentOS 8
CentOS (Community ENTerprise Operating System) was a free, open-source Linux distribution derived from the sources of Red Hat Enterprise Linux (RHEL). CentOS 8, released in September 2019, was part of the CentOS project’s effort to provide a robust, enterprise-grade operating system to the community.

However, in December 2020, Red Hat announced the end of life (EOL) for CentOS Linux 8 as of December 31, 2021, in favor of CentOS Stream, a rolling-release development version positioned between Fedora and RHEL.

## What is Rocky Linux?
Rocky Linux is a community-driven enterprise operating system designed to be 100% bug-for-bug compatible with RHEL. It was created as a direct replacement for CentOS Linux after Red Hat shifted focus. Founded by Gregory Kurtzer, a co-founder of CentOS, Rocky Linux aims to provide a stable, production-ready OS for servers and enterprise systems. Its mission is to remain community-maintained and freely available.

### Migration from CentOS 8 to Rocky Linux
Migrating from CentOS 8 to Rocky Linux is a straightforward process thanks to the compatibility between the two distributions. The Rocky Linux project provides a script to automate the transition, ensuring all packages are swapped cleanly with their Rocky equivalents.

## Prerequisites
You must be running CentOS 8 (not CentOS Stream).

Ensure all updates are installed:
```bash
sudo dnf update -y
```

Reboot if necessary.

## Migration Steps
1. Download the official migration script:
```bash
curl -O https://raw.githubusercontent.com/rocky-linux/rocky-tools/main/migrate/migrate2rocky.sh
```
2. Make the script executable:
```bash
chmod +x migrate2rocky.sh
```
3. Run the migration:
```bash
sudo bash migrate2rocky.sh -r
```
This script:
- Detects your current CentOS packages
- Replaces them with Rocky Linux equivalents
- Cleans up CentOS branding

4. Reboot the system:
```bash
sudo reboot
```
5. Verify the migration: After reboot, check the OS release:
```bash
cat /etc/os-release
```
## Notes
Back up your system before starting, especially if it's in a production environment.

This migration process is safe for most common setups but may require additional steps if using third-party repositories or custom kernels.

For enterprise environments, test the migration in a staging environment before applying to production.

