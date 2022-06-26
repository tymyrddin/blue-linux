# Choosing a firewall

With a firewall, you can:

* Log hosts scanning services that aren't running.
* Limit the services that programs can connect to.
* Segregate the local network into trust segments (Local Area Network (LAN), DeMilitarised Zone (DMZ), and Internet).
* Redirect ports to the hosts providing the service (Network address translation (NAT)).

If you need one for a personal PC at home, probably only the first two features are of interest. These are also the two that are most likely to cause issues for a beginning user. 

## Netfilter and iptables

Linux firewall code includes the netfilter architecture, which was introduced in stable kernel 2.4. For configuring netfilter through its own command line interface ([iptables](Netfilter-and-iptables.md)), one has to specify the behaviour of all IP packets that make up a connection both inward and outward. It requires extensive knowledge of TCP/IP protocols, but many tools have been developed to automate the configuration of netfilter and iptables. So [you have lots of choice](https://wiki.debian.org/Firewalls). 

## nftables

[nftables](NFTables.md) is the successor of iptables, and allows for much more flexible, scalable and performance packet classification.

## ufw and gufw

Recommended for beginners is [ufw and gufw](Gufw-and-ufw.md) because of its simplicity and ease of use. Gufw (GNU GPL v3) is for users bamboozled by firewalls. It has an easy to use interface for setting up inbound and outbound traffic rules for apps/services and ports. It is designed for beginners. Gufw is a GUI front-end to `ufw`, which is in itself a front-end to `netfilter` and `iptables`.
