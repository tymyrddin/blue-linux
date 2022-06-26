# Netfilter and iptables

## Installing persistence 

`iptables` is installed by default. For rules to be persistent (automatically loaded) so they work after reboot, install `iptables-persistent`:

    $ sudo apt-get install iptables-persistent
    [sudo] password for user: 
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following extra packages will be installed:
      netfilter-persistent
    The following NEW packages will be installed:
      iptables-persistent netfilter-persistent
    0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
    Need to get 18.9 kB of archives.
    After this operation, 147 kB of additional disk space will be used.

## Rules 

### Status command

To list rules -L showing interface name, rule options, TOS masks, packet and byte counters -n, and IP address and port in numeric format without using DNS to resolve names -v:
    
    # iptables -L -n -v

With line numbers (important for deleting or inserting new rules into the firewall):

    # iptables -n -L -v --line-numbers

To display INPUT or OUTPUT chain rules:

    # iptables -L INPUT -n -v
    # iptables -L OUTPUT -n -v --line-numbers

### Deleting a rule

To delete line number 4 using -D to delete one or more rules from the selected chain:

    # iptables -D INPUT 4

### Inserting a rule 

    # iptables -L INPUT -n --line-numbers
    Chain INPUT (policy DROP)
    num  target     prot opt source               destination
    1    DROP       all  --  xxx.xxx.xxx.1        0.0.0.0/0
    2    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state NEW,ESTABLISHED 

Inserting a rule between 1 and 2:

    # iptables -I INPUT 2 -s xxx.xxx.xxx.2 -j DROP

Gives:

    # iptables -L INPUT -n --line-numbers
    Chain INPUT (policy DROP)
    num  target     prot opt source               destination
    1    DROP       all  --  xxx.xxx.xxx.1        0.0.0.0/0
    2    DROP       all  --  xxx.xxx.xxx.2        0.0.0.0/0
    3    ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           state NEW,ESTABLISHED

### Saving the rules

For saving the rules so they can be loaded at every reboot (you need to have iptables-persistent installed)

    # iptables-save > /etc/iptables/rules.v4
    # ip6tables-save > /etc/iptables/rules.v6

### Stop/Restart

Some distros like CentOS have installed a service called `iptables` to start and stop the firewall and a configuration file to configure it. For all other distros, `iptables` is a command, not a service. 

## Configuring iptables
To set it to deny everything except the bare minimum requirements that you need on your system(s) and only accept connections that have been explicitly allowed in the rules. 

Localhost: 
    $ sudo iptables -A INPUT -i lo -j ACCEPT

Accept data related to outbound connections your system has initiated (this includes apt mirrors):

    $ sudo iptables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

You can set up tables for rules for traffic you wish to accept on your system from external connections:

    # iptables -N accept_traffic
    # iptables -A INPUT -j accept_traffic

You then can use it, for example on a server where you run SSH, with (change port to port you set):

    # iptables -A accept_traffic -p tcp --dport 22 -j ACCEPT

The two most common cracks posted on the Ubuntu forums are ssh and vnc, both running with password authentication. This probably is true for all debian-based distro's. You are recommended to secure ssh by using keys (and disabling password authentication) and either configuring iptables or using a service such as denyhosts or fail2ban.

To reject all traffic for which there are no rules set (the first way sends a Host Unreachable ICMP packet then terminates the connection, the second way simply ignores):

    # iptables -A INPUT -j REJECT --reject-with icmp-host-unreachable

or:

    # iptables -A INPUT -j DROP

## Configuring ip6tables
To set it to deny everything except the bare minimum requirements that you need on your system(s) and only accept connections that have been explicitly allowed in the rules: 

Localhost:

    $ sudo ip6tables -A INPUT -i lo -j ACCEPT

Accepting data related to outbound connections your system has initiated:

    $ sudo ip6tables -A INPUT -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT

Setting up a table:

    # ip6tables -N accept_traffic
    # ip6tables -A INPUT -j accept_traffic

Rejecting all traffic for which there are no rules set:

    # ip6tables -A INPUT -j REJECT --reject-with icmp6-addr-unreachable

or

    # ip6tables -A INPUT -j DROP

## Usage examples

### ICMP

For accepting "Time Exceeded" (necessary for time-restricted connection setups):

    $ sudo iptables -A INPUT -p icmp -m icmp --icmp-type 11 -j ACCEPT

For accepting "Destination Unreachable":

    $ sudo iptables -A INPUT -p icmp -m icmp --icmp-type 3/4 -j ACCEPT

For accepting PING requests/responses ("Echo" ICMP, for keep-alive requests):

    $ sudo iptables -A INPUT -p icmp -m icmp --icmp-type 8 -j ACCEPT

For IPv6 there are a kazillion ICMP requests so if you are not blocking IPv6, it is recommended to not block ICMP packets:

    $ sudo ip6tables -A INPUT -p icmpv6 -j ACCEPT 

