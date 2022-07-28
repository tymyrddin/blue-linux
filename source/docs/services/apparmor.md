# Application armour (AppArmor)

Application Armor (AppArmor) is a kernel-level Mandatory Access Control (MAC) feature that restricts applications from accessing 
classes of computer resources. For example, AppArmor can allow a word processor to read and write files to the local 
hard drive, but deny it to access the internet to send messages.

A common way to spread malware is to wrap it (or hide it) in some completely different type of file. An application 
like AppArmor can be configured to disallow these files any write or internet capabilities. Any malware in the file 
would not be able to copy itself or "call home" as a newly recruited botnet member.

[AppArmor](https://wiki.ubuntu.com/AppArmor) likely does not need much tuning for a standard desktop system as its 
default settings are good enough to fend off most malware attempts. 