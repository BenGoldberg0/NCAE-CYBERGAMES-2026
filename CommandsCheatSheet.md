### MikroTik
* List interfaces
  * `/interface print`
* Assign IP to interface
  * `/ip address add address=[address]/[cidr] interface=[interface]`
* List IP addresses associated with each interface
  * `/ip address print`
* Remove IP address
  * `/ip address remove numbers=[number from /ip address print]`
* Show routing table
  * `/ip route print`
* Add static route
  * `/ip route add dst-address=[network]/[cidr] gateway=[gateway]`
* DNS config
  * `/ip dns set servers=[dns1],[dns2]`
* Firewall rules list
  * `/ip firewall filter print`
* Export config (backup)
  * `/export file=[filename]`
* DHCP server leases
  * `/ip dhcp-server lease print`
* Stuff to do in the GUI (access using ip address of router on port 8080)
  * Set gateway to be the IP address of the device that links us to the internet
  * Enable "Bridge All LAN Ports"
  * Enable "NAT"
  * Click apply configuration
  * Click "Post Mapping" under NAT
  * Add mappings from the router on port 80 to be directed to web server address and web server port for TCP and UDP

### Linux network config
* Show IP addresses and their associated interfaces
  * `ip addr`
* Assign IP address to interface
  * `ip addr add [address]/[cidr] dev [interface]`
* Remove IP address from interface
  * `ip addr del [address]/[cidr] dev [interface]`
* Bring interface up/down
  * `ip link set [interface] up|down`
* Add default gateway
  * `ip route add default via [default gateway address]`
* Show IP routes
  * `ip route`
* ARP table
  * `ip neigh`

### Linux network troubleshooting
* Check listening ports
  * `ss -tulnp`
* DNS lookup
  * `dig [domain]` or `nslookup [domain]`
* Trace route
  * `traceroute [address]`
* Packet capture
  * `tcpdump -i [interface] -n`
* Test connectivity
  * `ping -c 4 [address]`

### Linux DNS config
* Edit resolv.conf (temporary)
  * `nano /etc/resolv.conf`
  * Add: `nameserver [dns_ip]`

### Linux firewall (iptables)
* List rules
  * `iptables -L -n -v`
* Allow incoming port
  * `iptables -A INPUT -p tcp --dport [port] -j ACCEPT`
* Block IP
  * `iptables -A INPUT -s [ip] -j DROP`
* NAT/masquerade (for routing)
  * `iptables -t nat -A POSTROUTING -o [wan_interface] -j MASQUERADE`
* Enable IP forwarding
  * `echo 1 > /proc/sys/net/ipv4/ip_forward`

### Linux apache webserver
* Starting the server
  * `systemctl start apache2`
* Check server status
  * `systemctl status apache2`
* Edit contents of website
  * `nano /var/www/html/index.html`

### Linux services (systemctl)
* Stop/restart/enable on boot
  * `systemctl stop|restart|enable [service]`
* View logs
  * `journalctl -u [service] -f`

### SSH
* Connect
  * `ssh [user]@[host]`
* Copy file to remote
  * `scp [file] [user]@[host]:[path]`
* Generate key pair
  * `ssh-keygen -t ed25519`

### nmap
* Basic port scan
  * `nmap [target]`
* Scan specific ports
  * `nmap -p [port1],[port2] [target]`
* Service/version detection
  * `nmap -sV [target]`
* OS detection
  * `nmap -O [target]`
* Aggressive scan (OS, version, scripts, traceroute)
  * `nmap -A [target]`
* Scan entire subnet
  * `nmap [network]/[cidr]`
* Stealth SYN scan
  * `nmap -sS [target]`
* UDP scan
  * `nmap -sU [target]`

### Common ports reference
* 22 - SSH
* 53 - DNS
* 80 - HTTP
* 443 - HTTPS
* 8080 - HTTP alt/proxies
* 3389 - RDP
* 21 - FTP
* 23 - Telnet
* 25 - SMTP
* 3306 - MySQL
* 5432 - PostgreSQL