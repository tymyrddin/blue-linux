# Rootkit scanner

A rootkit is a collection of tools a hacker installs on a victim's computer after gaining initial access. It generally consists of network sniffers, log-cleaning scripts, and trojaned replacements of core system utilities such as `ps`, `netstat`, `ifconfig`, and `killall`. Most times they are self-hiding toolkits to avoid the eye of the sysadmin. Applications that are used to detect rootkits are known as rootkit scanners. There are two rootkit scanners that are handy to have on your linux box: rkhunter and chkrootkit. Both. They may not stop a sophisticated adversary, they do help us detect some known infections and mistakes we have made. 

With rkhunter and chrootkit you can scan for known malware, viruses, and rootkits. Best protection is to run them regularly, like every week (or night), and have them send reports to you by local mail. You can also use them to scan a system when you see suspicious activity like high load, suspicious processes or when your machine suddenly starts to send malware. 

## Scanners 

* [chrootkit](chrootkit.md)
* [rkhunter](rkhunter.md) 
