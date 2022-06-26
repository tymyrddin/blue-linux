# Intrusion detection system (IDS)

You can use a firewall, keep your system software up to date, stop all non-required services, use long and difficult passwords and password managers, and more, and there is still a chance that some intruder might get into your system.

When intruders penetrate your system there is a great chance that they will want to make their presence as quiet as possible. To do so, they are most likely to replace some common binaries such as `ls`, `netstat` or `ps` with versions that will hide their presence. 

For example, `ls` can be replaced with an `ls` version that won't show the files they created, `netstat` will not show connections that are used by the intruder, and `ps` will hide processes the intruder runs. To detect changes like that in your system, set up intrusion detection. 

* [Choosing an IDS](Choosing-an-IDS.md)
* [Tripwire](Tripwire.md)
* [Aide](Aide.md)

