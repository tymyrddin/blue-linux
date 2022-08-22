# Introduction

There are many types of devices and mechanisms within the security environment to provide a layered approach of defense. 
This is so that if an attacker is able to bypass one layer, another layer stands in the way to protect the network. 
Two of the most popular and significant tools used to secure networks are firewalls and intrusion detection systems. 

## Choosing a firewall for a GNU/Linux

With a firewall, you can:

* Log hosts scanning services that aren't running.
* Limit the services that applications can connect to.
* Segregate the local network into trust segments (Local Area Network (LAN), DeMilitarised Zone (DMZ), and Internet).
* Redirect ports to the hosts providing the service (Network address translation (NAT)).

If you need one for a personal PC at home, probably only the first two features are of interest. These are also the two 
that are most likely to cause issues for a beginning user. 

* Linux firewall code includes the netfilter architecture, which was introduced in stable kernel 2.4. For configuring netfilter through its own command line interface ([iptables](netfilter-and-iptables.md)), one has to specify the behaviour of all IP packets that make up a connection both inward and outward. It requires extensive knowledge of TCP/IP protocols, but many tools have been developed to automate the configuration of netfilter and iptables. So [you have lots of choice](https://wiki.debian.org/Firewalls). 
* [nftables](nftables.md) is the successor of iptables, and allows for much more flexible, scalable and performance packet classification.
* Recommended for beginners is [ufw and gufw](gufw-and-ufw.md) because of its simplicity and ease of use. Gufw (GNU GPL v3) is for users bamboozled by firewalls. It has an easy-to-use interface for setting up inbound and outbound traffic rules for apps/services and ports. It is designed for beginners. Gufw is a GUI front-end to `ufw`, which is in itself a front-end to `netfilter` and `iptables`.

## Choosing a HIDS for a GNU/Linux

Most of the [HIDS tools for Linux](ids.md) are File Integrity Agents (FIAs) and use Error Detection algorithms. A FIA 
monitors the integrity and state of the files and objects on a machine. It creates a hash of all files to be monitored. 
That snapshot is periodically checked against the current hash of the files. If it detects changes to those files, then 
it alerts the administrator that an unauthorised access or change has taken place. 

* [Aide](aide.md) is such a FIA, entirely open source and licensed via the GPL and easy in its configuration. For a Home PC, Aide will 
do.
* [Tripwire](tripwire.md)
* [OSSEC](ossec.md) monitors the checksum signatures of all the log files to detect possible interference and any 
attempts to get to the root account.

## Related attack trees

* [Scanning](attack-trees:docs/scanning/README)
* [Malware](attack-trees:docs/malware/README)
* [System](attack-trees:docs/system/README)
* [Network](https://tymyrddin.github.io/red-network/)