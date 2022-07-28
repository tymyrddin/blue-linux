# Design principles and sudo killers

GNU/Linux was built as a multi-user operating system from the start with two important principles: 

* The Least Privilege principle states that any entity, user or otherwise, should only be granted the minimum amount of 
privileges required to do its job and no more. 
* The second, equally important principle, is Isolation. This is implemented in user separation. The activities of one user
should not be allowed to affect other users, and data belonging to one user should not be accessible to another user 
unless specifically allowed.

Most GNU/Linux distributions create a non-privileged user account for daily use, but one can use `sudo` or download an 
and install an app to do things as administrator in desktop applications. With the users' password!

While the sudo system does not give unbridled root permissions, if an attacker has a limited shell that has access to 
certain programs using the command sudo he/she might be able to abuse sudo to escalate privileges.

The [sudo killer tool](https://github.com/TH3xACE/SUDO_KILLER) helps to identify misconfiguration within sudo rules, vulnerability within the version of sudo being used 
(CVEs and vulns) and the uses of dangerous binary, all of these could be abuse to elevate privilege to `root`.

* The tool will provide a list of commands or local exploits which could be exploited to elevate privilege.
* It does not perform any exploitation on your behalf, the exploitation will need to be performed manually and this is 
intended. Both red and blue team can use it to their benefit.

## Installation 

Preferably on a kali machine.

To pull from docker:

    service docker start 
    docker pull th3xace/sudo_killer_demo 
    docker run –rm -it th3xace/sudo_killer_demo

To build locally using the Dockerfile:

    service docker start 
    git clone https://github.com/TH3xACE/SUDO_KILLER.git 
    cd SUDO_KILLER 
    docker build -t th3xace/sudo_killer_demo . 
    docker run –rm -it th3xace/sudo_killer_demo

Download: https://github.com/TH3xACE/SUDO_KILLER

## Command usage

    ./sudo_killer.sh -c -r report.txt -e /tmp/

Arguments:

    k : Keywords 
    e : export location (export /etc/sudoers) 
    c : include CVE checks with respect to sudo version 
    s : supply user password for sudo checks (not recommended ++except for CTF) 
    r : report name (save the output) 
    h : help

If you need to input a password to run `sudo -l` then the script will not work if you don’t provide a password with the 
argument `-s`.

sudo_killer does not exploit automatically by itself, it was designed to check for misconguration and vulnerabilities 
and then offer:

* a list of commands to exploit
* a list of exploits
* some description on how and why the attack could be performed

## CVEs check

To update the CVE database: 

    ./cve_update.sh

## Disclaimer

This script is for Educational purpose ONLY. Do not use it without permission. The usual disclaimer applies, especially 
the fact that TH3xACE is not liable for any damages caused by direct or indirect use of the information or functionality 
provided by these programs.