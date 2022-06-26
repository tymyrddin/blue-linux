# Modifying kernel parameters

There are three ways to pass options to the kernel and thus control its behaviour:
    
* When building the kernel.
* When starting the kernel (usually when invoked from a boot loader).
* At runtime (through the files in `/proc` and `/sys`).

`sysctl` is an interface for examining and changing kernel parameters at runtime and is a near-necessary tool in the defense from [[en:hacking:malware:start|malware]]. It allows you to make changes to a running Linux kernel. With `/etc/sysctl.conf` you can configure various Linux networking and system settings such as:

* Limit network-transmitted configuration for IPv4
* Limit network-transmitted configuration for IPv6
* Turn on execshield protection
* Prevent against the common ‘syn flood attack’
* Turn on source IP address verification
* Preventing a cracker from using a spoofing attack against the IP address of the server.
* Logging several types of suspicious packets, such as spoofed packets, source-routed packets, and redirects.

## Sysctl interface

* [Altering sysctl configuration](Altering-sysctl-configuration.md)
* [Spoof protection](Spoof-protection.md)
* [SYN cookies](SYN-cookies.md)
* [Packet forwarding](Packet-forwarding.md)
* [ICMP redirects](ICMP-redirects.md)
* [Single Ring Recovery](Single-Ring-Recovery.md)
* [Logging](Logging.md)
* [Magic SysRq key](Magic-SysRq-key.md)
* [Protected links](Protected-links.md)
