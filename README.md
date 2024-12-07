
# Nmap Command Examples

## General Scanning

- **Scan a single IP**  
  `nmap 192.168.1.1`

- **Scan specific IPs**  
  `nmap 192.168.1.1 192.168.2.1`

- **Scan a range of IPs**  
  `nmap 192.168.1.1-254`

- **Scan a domain**  
  `nmap scanme.nmap.org`

- **Scan using CIDR notation**  
  `nmap 192.168.1.0/24`

- **Scan targets from a file**  
  `nmap -iL targets.txt`

- **Scan 100 random hosts**  
  `nmap -iR 100`

- **Exclude specific hosts**  
  `nmap --exclude 192.168.1.1`

## Host Discovery

- **List targets without scanning**  
  `nmap 192.168.1.1-3 -sL`

- **Disable port scanning and only perform host discovery**  
  `nmap 192.168.1.1/24 -sn`

- **Disable host discovery and only perform port scan**  
  `nmap 192.168.1.1-5 -Pn`

- **TCP SYN discovery on specific ports**  
  `nmap 192.168.1.1-5 -PS22-25,80`

- **TCP ACK discovery on specific ports**  
  `nmap 192.168.1.1-5 -PA22-25,80`

- **UDP discovery on a specific port**  
  `nmap 192.168.1.1-5 -PU53`

- **ARP discovery on local network**  
  `nmap 192.168.1.1-1/24 -PR`

- **Disable DNS resolution**  
  `nmap 192.168.1.1 -n`

## Port Specification

- **Scan a specific port**  
  `nmap 192.168.1.1 -p 21`

- **Scan a range of ports**  
  `nmap 192.168.1.1 -p 21-100`

- **Scan multiple TCP and UDP ports**  
  `nmap 192.168.1.1 -p U:53,T:21-25,80`

- **Scan all ports**  
  `nmap 192.168.1.1 -p-`

- **Scan ports by service name**  
  `nmap 192.168.1.1 -p http,https`

- **Fast port scan (100 most common ports)**  
  `nmap 192.168.1.1 -F`

- **Scan the top 2000 ports**  
  `nmap 192.168.1.1 --top-ports 2000`

- **Scan from port 1 to port 65535**  
  `nmap 192.168.1.1 -p-65535`

- **Scan from port 0 to port 65535**  
  `nmap 192.168.1.1 -p0-`

## OS Detection

- **Remote OS detection using TCP/IP stack fingerprinting**  
  `nmap 192.168.1.1 -O`

- **Limit OS scan to hosts with open and closed TCP ports**  
  `nmap 192.168.1.1 -O --osscan-limit`

- **Aggressively guess the OS**  
  `nmap 192.168.1.1 -O --osscan-guess`

- **Set the maximum number of OS detection tries**  
  `nmap 192.168.1.1 -O --max-os-tries 1`

- **Enable OS detection, version detection, script scanning, and traceroute**  
  `nmap 192.168.1.1 -A`

## Service and Version Detection

- **Determine the version of the service running on a port**  
  `nmap 192.168.1.1 -sV`

- **Set version detection intensity level (0-9)**  
  `nmap 192.168.1.1 -sV --version-intensity 8`

- **Enable light version detection (faster but less accurate)**  
  `nmap 192.168.1.1 -sV --version-light`

- **Enable full version detection (slower but more accurate)**  
  `nmap 192.168.1.1 -sV --version-all`

- **Enable OS detection, version detection, script scanning, and traceroute**  
  `nmap 192.168.1.1 -A`

## NSE Scripts

- **Scan with default NSE scripts**  
  `nmap 192.168.1.1 -sC`

- **Scan with default NSE scripts (alternative)**  
  `nmap 192.168.1.1 --script default`

- **Scan with a specific script (e.g., banner)**  
  `nmap 192.168.1.1 --script=banner`

- **Scan with a wildcard for scripts (e.g., http*)**  
  `nmap 192.168.1.1 --script=http*`

- **Scan with multiple specific scripts (e.g., http and banner)**  
  `nmap 192.168.1.1 --script=http,banner`

- **Scan with default scripts but exclude intrusive ones**  
  `nmap 192.168.1.1 --script "not intrusive"`

- **Run an NSE script with arguments (e.g., SNMP)**
  ```bash
  nmap 192.168.1.1 --script snmp-sysdescr --script-args snmpcommunity=admin
