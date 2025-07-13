# Nmap Commands Reference Repository

A comprehensive collection of nmap commands organized by functionality and use case.

## Table of Contents
- [Target Specification](#target-specification)
- [Scan Types](#scan-types)
- [Port Scanning](#port-scanning)
- [OS Detection](#os-detection)
- [Version Detection](#version-detection)
- [Service Detection](#service-detection)
- [Script Scanning](#script-scanning)
- [Output Options](#output-options)
- [Performance & Timing](#performance--timing)
- [Advanced Techniques](#advanced-techniques)
- [Common Use Cases](#common-use-cases)

---

## Target Specification

### Single Target
```bash
# Scan a single IP address
nmap 192.168.1.1

# Scan a hostname
nmap example.com

# Scan using FQDN
nmap www.example.com
```

### Multiple Targets
```bash
# Scan multiple IPs
nmap 192.168.1.1 192.168.1.2 192.168.1.3

# Scan IP range with dash notation
nmap 192.168.1.1-254

# Scan subnet using CIDR notation
nmap 192.168.1.0/24

# Scan multiple subnets
nmap 192.168.1.0/24 192.168.2.0/24
```

### Target Lists
```bash
# Scan targets from file
nmap -iL targets.txt

# Exclude specific targets
nmap 192.168.1.0/24 --exclude 192.168.1.1

# Exclude targets from file
nmap 192.168.1.0/24 --excludefile exclude.txt
```

### Wildcard Scanning
```bash
# Scan using wildcards
nmap 192.168.1.*

# Scan using octet ranges
nmap 192.168.1.1-10,20-30
```

---

## Scan Types

### TCP Scans
```bash
# TCP SYN scan (default, stealthy)
nmap -sS 192.168.1.1

# TCP Connect scan (complete handshake)
nmap -sT 192.168.1.1

# TCP ACK scan (firewall detection)
nmap -sA 192.168.1.1

# TCP Window scan
nmap -sW 192.168.1.1

# TCP FIN scan
nmap -sF 192.168.1.1

# TCP NULL scan
nmap -sN 192.168.1.1

# TCP Xmas scan
nmap -sX 192.168.1.1
```

### UDP Scans
```bash
# UDP scan
nmap -sU 192.168.1.1

# Combined TCP and UDP scan
nmap -sS -sU 192.168.1.1
```

### Other Scan Types
```bash
# Ping scan (host discovery only)
nmap -sn 192.168.1.0/24

# List scan (no packets sent)
nmap -sL 192.168.1.0/24

# Idle scan (zombie scan)
nmap -sI zombie_host:port target_host

# IP protocol scan
nmap -sO 192.168.1.1
```

---

## Port Scanning

### Port Selection
```bash
# Scan specific port
nmap -p 80 192.168.1.1

# Scan multiple ports
nmap -p 80,443,8080 192.168.1.1

# Scan port range
nmap -p 1-1000 192.168.1.1

# Scan all ports
nmap -p- 192.168.1.1

# Scan top 1000 ports (default)
nmap 192.168.1.1

# Scan most common ports
nmap --top-ports 100 192.168.1.1
```

### Protocol-Specific Ports
```bash
# Scan TCP ports only
nmap -p T:80,443 192.168.1.1

# Scan UDP ports only
nmap -p U:53,161 192.168.1.1

# Scan both TCP and UDP
nmap -p T:80,443,U:53,161 192.168.1.1
```

### Fast Scanning
```bash
# Fast scan (100 most common ports)
nmap -F 192.168.1.1

# Scan specific port ranges quickly
nmap -p 1-100 -T4 192.168.1.1
```

---

## OS Detection

### Basic OS Detection
```bash
# Enable OS detection
nmap -O 192.168.1.1

# Aggressive OS detection
nmap -O --osscan-guess 192.168.1.1

# OS detection with version detection
nmap -O -sV 192.168.1.1
```

### OS Detection Options
```bash
# Limit OS detection to promising targets
nmap -O --osscan-limit 192.168.1.0/24

# Maximum OS detection attempts
nmap -O --max-os-tries 2 192.168.1.1

# OS detection without port scan
nmap -O -sn 192.168.1.1
```

---

## Version Detection

### Basic Version Detection
```bash
# Version detection
nmap -sV 192.168.1.1

# Version detection with intensity
nmap -sV --version-intensity 9 192.168.1.1

# Light version detection
nmap -sV --version-light 192.168.1.1
```

### Version Detection Options
```bash
# All version detection probes
nmap -sV --version-all 192.168.1.1

# Trace version detection
nmap -sV --version-trace 192.168.1.1

# Version detection on specific ports
nmap -sV -p 80,443 192.168.1.1
```

---

## Service Detection

### Basic Service Detection
```bash
# Service detection with default scripts
nmap -sC 192.168.1.1

# Service detection with version detection
nmap -sC -sV 192.168.1.1

# Aggressive service detection
nmap -A 192.168.1.1
```

### Service Enumeration
```bash
# HTTP service enumeration
nmap -p 80 --script http-enum 192.168.1.1

# SMB service enumeration
nmap -p 445 --script smb-enum-* 192.168.1.1

# DNS service enumeration
nmap -p 53 --script dns-* 192.168.1.1

# SSH service enumeration
nmap -p 22 --script ssh-* 192.168.1.1
```

### Database Services
```bash
# MySQL enumeration
nmap -p 3306 --script mysql-* 192.168.1.1

# PostgreSQL enumeration
nmap -p 5432 --script pgsql-* 192.168.1.1

# MongoDB enumeration
nmap -p 27017 --script mongodb-* 192.168.1.1

# Redis enumeration
nmap -p 6379 --script redis-* 192.168.1.1
```

---

## Script Scanning

### Default Scripts
```bash
# Run default scripts
nmap -sC 192.168.1.1

# Run specific script
nmap --script script-name 192.168.1.1

# Run script category
nmap --script discovery 192.168.1.1
```

### Script Categories
```bash
# Safe scripts
nmap --script safe 192.168.1.1

# Intrusive scripts
nmap --script intrusive 192.168.1.1

# Vulnerability scripts
nmap --script vuln 192.168.1.1

# Malware detection scripts
nmap --script malware 192.168.1.1

# Authentication scripts
nmap --script auth 192.168.1.1
```

### Popular Scripts
```bash
# Vulnerability scan
nmap --script vuln 192.168.1.1

# Web application scan
nmap --script http-* 192.168.1.1

# SSL/TLS analysis
nmap --script ssl-* 192.168.1.1

# Brute force attacks
nmap --script brute 192.168.1.1
```

---

## Output Options

### Output Formats
```bash
# Normal output
nmap -oN scan_results.txt 192.168.1.1

# XML output
nmap -oX scan_results.xml 192.168.1.1

# Grepable output
nmap -oG scan_results.gnmap 192.168.1.1

# All output formats
nmap -oA scan_results 192.168.1.1
```

### Verbosity Options
```bash
# Verbose output
nmap -v 192.168.1.1

# Very verbose output
nmap -vv 192.168.1.1

# Debug output
nmap -d 192.168.1.1

# Packet trace
nmap --packet-trace 192.168.1.1
```

---

## Performance & Timing

### Timing Templates
```bash
# Paranoid (very slow)
nmap -T0 192.168.1.1

# Sneaky (slow)
nmap -T1 192.168.1.1

# Polite (slower)
nmap -T2 192.168.1.1

# Normal (default)
nmap -T3 192.168.1.1

# Aggressive (faster)
nmap -T4 192.168.1.1

# Insane (very fast)
nmap -T5 192.168.1.1
```

### Custom Timing
```bash
# Custom timing options
nmap --min-rate 1000 --max-rate 5000 192.168.1.1

# Parallel scanning
nmap --min-parallelism 100 --max-parallelism 256 192.168.1.1

# Timeout options
nmap --host-timeout 30m 192.168.1.1
```

---

## Advanced Techniques

### Stealth Scanning
```bash
# Stealth SYN scan with random data
nmap -sS -D RND:10 192.168.1.1

# Fragment packets
nmap -f 192.168.1.1

# Use decoys
nmap -D 192.168.1.100,192.168.1.101,ME 192.168.1.1

# Spoof source address
nmap -S 192.168.1.100 192.168.1.1
```

### Firewall Evasion
```bash
# ACK scan for firewall detection
nmap -sA 192.168.1.1

# Fragment packets
nmap -f -f 192.168.1.1

# Use specific MTU
nmap --mtu 24 192.168.1.1

# Append random data
nmap --data-length 200 192.168.1.1
```

### IPv6 Scanning
```bash
# IPv6 scan
nmap -6 2001:db8::1

# IPv6 ping scan
nmap -6 -sn 2001:db8::/32

# IPv6 with specific interface
nmap -6 -e eth0 2001:db8::1
```

---

## Common Use Cases

### Network Discovery
```bash
# Discover live hosts
nmap -sn 192.168.1.0/24

# Quick network scan
nmap -T4 -F 192.168.1.0/24

# Comprehensive network scan
nmap -T4 -A -v 192.168.1.0/24
```

### Web Server Scanning
```bash
# Basic web server scan
nmap -p 80,443 --script http-* 192.168.1.1

# SSL/TLS analysis
nmap -p 443 --script ssl-* 192.168.1.1

# Web vulnerability scan
nmap -p 80,443 --script http-vuln-* 192.168.1.1
```

### Database Scanning
```bash
# Database port scan
nmap -p 1433,1521,3306,5432 192.168.1.1

# MySQL comprehensive scan
nmap -p 3306 --script mysql-* 192.168.1.1

# Database vulnerability scan
nmap -p 1433,1521,3306,5432 --script vuln 192.168.1.1
```

### Security Assessment
```bash
# Vulnerability assessment
nmap --script vuln 192.168.1.1

# Complete security scan
nmap -T4 -A --script vuln 192.168.1.1

# Penetration testing scan
nmap -T4 -A --script "not intrusive" 192.168.1.1
```

---

## Tips and Best Practices

### Performance Tips
- Use `-T4` for faster scans in most environments
- Limit port ranges for faster results
- Use `--top-ports` for quick assessments
- Consider parallel scanning with `--min-parallelism`

### Stealth Tips
- Use `-sS` for stealth SYN scans
- Fragment packets with `-f`
- Use timing template `-T1` or `-T2` for stealth
- Employ decoys with `-D`

### Accuracy Tips
- Use `-sV` for service version detection
- Enable OS detection with `-O`
- Run vulnerability scripts with `--script vuln`
- Use `-A` for aggressive scanning (OS, version, script, traceroute)

### Output Tips
- Always save results with `-oA`
- Use `-v` for verbose output during scanning
- Consider XML output for parsing results
- Use grepable output for quick analysis

---

## Legal and Ethical Considerations

**Important**: Only use these commands on networks and systems you own or have explicit permission to test. Unauthorized network scanning may violate laws and regulations in your jurisdiction.

## Contributing

Feel free to contribute additional commands, use cases, or improvements to this repository. Please ensure all contributions follow ethical guidelines and include appropriate warnings where necessary.

## License

This repository is provided for educational and authorized testing purposes only.