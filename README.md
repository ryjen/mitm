
## MITM Demo

This demonstration will perform two types of man-in-the-middle attacks:

1.  ARP spoofing
2.  DNS spoofing

An HTTP proxy is used to intercept websites and inject javascript.

A network sniffer is used to read authentication information.

### Environment:

1. VirtualBox hardware abstraction
2. NAT Network abstraction

### Actors:

1. Linux as the Attacker
2. Windows 10 as the Victim

### Attacker Configuration:

1. IP Forwarding Enabled
2. `ip` and `nmap` commands
2. Bettercap installed (improved Ettercap)

