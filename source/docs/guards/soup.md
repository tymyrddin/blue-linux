# Alphabet soup

## Firewall

* A firewall implements rules that prevent network traffic based on protocol, source/destination address, and/or 
source/destination port. Firewalls can implement access control lists and prevent the use of insecure protocols, 
such as blocking all traffic on TCP port 23 (Telnet’s default port).

## IDS

An IDS platform can analyse network traffic for patterns and recognize malicious attack patterns. It can create notifications, but it can not block the unwanted packets from entering the network.
* IDS can be deployed either at the host level or the network level.
  * Host-based monitors (and protects) the specific host (for example a single PC) it is installed on. For example, a HIDS will look at log and config files for any unexpected rewrites.
  * Network-based focuses on protecting an entire network. Usually, dedicated hardware appliances run such software. For example, a NIDS will look at the checksums in captured packets and message authentication integrity of systems such as SHA1.
* The fact that a NIDS is usually installed on a stand-alone piece of equipment means that it doesn’t drag down the 
processors of servers or PC's. The activity of HIDS is not as aggressive as that of NIDS and can be implemented by a 
lightweight daemon on the computer which does not burn up too much CPU. Neither system generates extra network traffic.
* In addition to the two main types of IDS, there are also two main subsets of these IDS types:
  * Signature-based Intrusion Detection System (SBIDS). An SBNIDS for example, tracks all the packets passing over the network and then compares them to a database containing attributes or signatures of familiar malicious threats.
  * Anomaly-based Intrusion Detection System (ABIDS). An ABNIDS for example, tracks the traffic of a network and then 
compares it to an established measure (which could be machine learning based) and this allows the system to find what 
is normal for the network in terms of Ports, Protocols, Bandwidth, and other devices, thereby quickly alerting 
administrators about any unusual or potentially malicious activity in the network.

## IPS

IPS combines the analysis functionality of an IDS with the ability to intervene and prevent the delivery of malicious packets.
* IPS interact with firewalls and software applications by adjusting settings.
* Incorrectly calibrated IPSs can cause havoc and bring your legitimate network activity to a halt.

