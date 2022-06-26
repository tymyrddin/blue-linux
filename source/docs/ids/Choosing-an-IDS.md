# Choosing an IDS

Most of these IDS tools, like aide and tripwire, are File Integrity Agents (FIAs) and use Error Detection algorithms. 

A FIA monitors the integrity and state of the files and objects on a machine. It creates a hash of all files to be monitored. That snapshot is periodically checked against the current hash of the files. If it detects changes to those files, then it alerts the administrator that an unauthorised access or change has taken place. 

One of the key differences between [Tripwire](Tripwire.md) and [Aide](Aide.md) is their commercial status. Aide is entirely open source and licensed via the GPL and much, much easier in its configuration. Tripwire offers extended features that can make it more secure than Aide on servers, but storing aide databases on an encrypted filesystem on another machine (or an external drive) can be considered good enough to not need tripwire's extended feature(s) for a PC (Not that you can not sign the databases AND put them on another machine or external drive).

## Common

If you are not being targeted by petty tyrants, but are merely watched over by dragnet surveillance (like all of us are) and concerned about that, and you do want IDS and have minimal technical skills, I recommend using Aide.

## Needing more than that 
When being **targeted**, neither will do. 

Tripwire nor aide have built-in support for (centralised) logging and management that would allow delivering a service for guarding machines of non-technically inclined people. Ossec, Osiris and Samhain do have logging and management, but I have found no intelligent tree traversing for anomaly detection (yet) that would allow for the discovery of (new) (types of) malware and attacks. 

Ossec, Osiris and Samhain are promising in terms of being able to support the delivery of a //hacking forensics service// and //digital resilience workshops// for activists, and for developing some anomaly detection intelligence modules. I will be trying out all three. Please stand by.
