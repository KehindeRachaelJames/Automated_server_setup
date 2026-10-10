# Automated Server Setup

This is a simple Bash script that automates the initial setup of a Linux server. It updates system packages, installs Nginx, and starts the Nginx service.

The goal is to make the basic setup process quicker and easier, without having to run each command manually.

## Features

- Detects the Linux distribution and selects the appropriate package manager.
- Updates installed system packages.
- Installs Nginx and its dependencies.
- Enables Nginx to start automatically on boot.
- Includes a dry-run mode to preview commands before making changes.

## Supported Systems

The script supports Debian/Ubuntu-based and Fedora/RHEL-based Linux distributions using APT, DNF, or YUM.

## Getting Started

Clone the repository:

```bash
git clone <repository-url>
cd <repository-directory>
```

Make the script executable:

```bash
chmod +x setup-server.sh
```

## Usage

### Preview the setup

Run a dry run to see which commands would be executed without making changes to your system.

```bash
./setup-server.sh --dry-run
```

You can also preview commands for a specific package manager:

```bash
./setup-server.sh --dry-run --package-manager apt
```

Replace `apt` with `dnf` or `yum` if needed. This is useful when previewing commands for a different Linux environment.

### Run the setup

When you're ready, run the script with root privileges:

```bash
sudo ./setup-server.sh
```

The script will update your system packages, install Nginx, and enable and start the service.

### Other options

Display the available options:

```bash
./setup-server.sh --help
```

| Option | Description |
|---|---|
| `--dry-run` | Preview commands without executing them. |
| `--package-manager` | Choose a package manager for dry runs only. |
| `--help` | Display usage information. |

## Verify the Installation

Once the script finishes, check that Nginx is running:

```bash
systemctl status nginx
```

You can also open `http://<server-ip-address>` in your browser to check whether the default Nginx page is accessible. This requires the relevant network and firewall rules to allow HTTP traffic.

## Summary

- Root privileges are required for a normal setup.
- The script upgrades installed packages, which may affect existing workloads.
- Dry-run mode previews commands but does not verify that the installation will succeed.
- The script does not configure firewalls, HTTPS, or Nginx virtual hosts.
