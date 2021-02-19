
## MITM Scenario

### Environment:

1. VirtualBox hardware abstraction
2. Private network abstraction

### Actors:

1. Linux as the Attacker
2. Windows 10 as the Victim
3. Linux/NGINX as the server

### Attacker Configuration:

1. IP Forwarding Enabled
2. `ip` and `nmap` commands
2. Bettercap installed (improved Ettercap)

### Automation

1. Vagrant infrastructure setup
2. Attacker script
    - scan router
    - scan potential victims
    - initiate attack
3. main script for all of the above
