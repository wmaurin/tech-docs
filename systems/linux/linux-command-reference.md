# Linux Command Reference

## File & Directory Operations

```bash
# Navigation
pwd                          # Print working directory
cd <directory>               # Change directory
cd ..                        # Go up one level
cd ~                         # Go to home directory
cd -                         # Go to previous directory

# Listing
ls                           # List files
ls -la                       # List all with details
ls -lh                       # Human-readable sizes
ls -lt                       # Sort by modification time

# File operations
cp <source> <dest>           # Copy file
cp -r <source> <dest>        # Copy directory
mv <source> <dest>           # Move/rename
rm <file>                    # Remove file
rm -r <directory>            # Remove directory
rm -rf <directory>           # Force remove

# Directory operations
mkdir <name>                 # Create directory
mkdir -p <path/to/dir>       # Create nested directories
rmdir <name>                 # Remove empty directory

# File creation
touch <file>                 # Create empty file
```

## File Viewing & Editing

```bash
# Viewing files
cat <file>                   # Display entire file
less <file>                  # Paginated view
head <file>                  # First 10 lines
head -n 20 <file>            # First 20 lines
tail <file>                  # Last 10 lines
tail -f <file>               # Follow file changes

# Text editors
nano <file>
vim <file>
```

## Searching

```bash
# Find files
find <path> -name "*.txt"                # By name
find <path> -type f                      # Files only
find <path> -type d                      # Directories only
find <path> -mtime -7                    # Modified in last 7 days
find <path> -size +100M                  # Larger than 100MB

# Search file contents
grep "pattern" <file>
grep -r "pattern" <directory>            # Recursive
grep -i "pattern" <file>                 # Case insensitive
grep -n "pattern" <file>                 # Show line numbers
grep -v "pattern" <file>                 # Invert match

# Locate files (uses database)
locate <filename>
updatedb                                 # Update locate database
```

## Permissions & Ownership

```bash
# Change permissions
chmod 755 <file>             # rwxr-xr-x
chmod +x <file>              # Add execute
chmod -w <file>              # Remove write
chmod -R 755 <directory>     # Recursive

# Change ownership
chown <user> <file>
chown <user>:<group> <file>
chown -R <user>:<group> <directory>
```

## Process Management

```bash
# View processes
ps aux                       # All processes
ps aux | grep <name>         # Filter processes
top                          # Interactive process viewer
htop                         # Better process viewer

# Process control
kill <pid>                   # Terminate process
kill -9 <pid>                # Force kill
killall <name>               # Kill by name
pkill <pattern>              # Kill by pattern

# Background jobs
<command> &                  # Run in background
jobs                         # List background jobs
fg                           # Bring to foreground
bg                           # Continue in background
nohup <command> &            # Persist after logout
```

## Disk & Storage

```bash
# Disk usage
df -h                        # Filesystem usage
du -sh <directory>           # Directory size
du -sh *                     # Size of each item
du -h --max-depth=1          # One level deep

# Disk management
lsblk                        # List block devices
mount <device> <mountpoint>
umount <mountpoint>
```

## Networking

```bash
# Network information
ip addr                      # IP addresses
ip route                     # Routing table
hostname                     # Show hostname
hostname -I                  # Show IP addresses

# Connectivity
ping <host>
curl <url>
wget <url>

# Ports & connections
ss -tuln                     # Listening ports
netstat -tuln                # Listening ports (older)
lsof -i :<port>              # Process using port
```

## System Information

```bash
# System info
uname -a                     # Kernel information
cat /etc/os-release          # OS information
uptime                       # System uptime
whoami                       # Current user
id                           # User and group IDs

# Hardware info
free -h                      # Memory usage
lscpu                        # CPU information
```

## Archives & Compression

```bash
# tar archives
tar -cvf archive.tar <files>             # Create
tar -xvf archive.tar                     # Extract
tar -czvf archive.tar.gz <files>         # Create gzipped
tar -xzvf archive.tar.gz                 # Extract gzipped
tar -tzvf archive.tar.gz                 # List contents

# zip
zip -r archive.zip <directory>
unzip archive.zip
```

## Text Processing

```bash
# Basic tools
wc -l <file>                 # Count lines
sort <file>                  # Sort lines
uniq                         # Remove duplicates
cut -d',' -f1 <file>         # Cut columns
awk '{print $1}' <file>      # Print first column
sed 's/old/new/g' <file>     # Find and replace
```

## Package Management

```bash
# Debian/Ubuntu (apt)
apt update                   # Update package list
apt upgrade                  # Upgrade packages
apt install <package>
apt remove <package>
apt search <package>

# RHEL/CentOS (dnf/yum)
dnf update
dnf install <package>
dnf remove <package>
dnf search <package>
```

## SSH & Remote

```bash
# Connect
ssh <user>@<host>
ssh -p <port> <user>@<host>
ssh -i <keyfile> <user>@<host>

# Copy files
scp <file> <user>@<host>:<path>
scp <user>@<host>:<path> <local>
scp -r <directory> <user>@<host>:<path>

# SSH key management
ssh-keygen -t ed25519
ssh-copy-id <user>@<host>
```

## Systemd Services

```bash
# Service management
systemctl start <service>
systemctl stop <service>
systemctl restart <service>
systemctl status <service>
systemctl enable <service>   # Start on boot
systemctl disable <service>

# View logs
journalctl -u <service>
journalctl -u <service> -f   # Follow logs
journalctl -u <service> --since "1 hour ago"
```

