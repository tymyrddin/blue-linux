# Postfix

## Installing 

  * [Postfix on Debian](https://wiki.debian.org/Postfix)
  * [Postfix on Archlinux](https://wiki.archlinux.org/index.php/Postfix)
  * [Postfix on Gentoo](https://wiki.gentoo.org/wiki/Postfix)
  * Fedora comes with RPMs for both Sendmail and Postfix. The default configuration is to use Sendmail, but you can [switch to Postfix](https://fedoraproject.org/wiki/Extras/SwitchingToPostfix). 

## Switching to postfix on Fedora

Installing postfix:

    $ sudo dnf install postfix
    [sudo] password for nina: 
    Last metadata expiration check: 1:12:16 ago on Thu 29 Mar 2018 08:33:58 PM CEST.
    Dependencies resolved.
    ================================================================================
     Package         Arch           Version                   Repository       Size
    ================================================================================
    Installing:
     postfix         x86_64         2:3.2.5-1.fc26            updates         1.4 M

    Transaction Summary
    ================================================================================
    Install  1 Package

    Total download size: 1.4 M
    Installed size: 4.0 M
    Is this ok [y/N]: Y
    Downloading Packages:
    postfix-3.2.5-1.fc26.x86_64.rpm                 1.4 MB/s | 1.4 MB     00:01    
    --------------------------------------------------------------------------------
    Total                                           475 kB/s | 1.4 MB     00:03     
    Running transaction check
    Transaction check succeeded.
    Running transaction test
    Transaction test succeeded.
    Running transaction
      Preparing        :                                                        1/1 
      Running scriptlet: postfix-2:3.2.5-1.fc26.x86_64                          1/1 
      Installing       : postfix-2:3.2.5-1.fc26.x86_64                          1/1 
      Running scriptlet: postfix-2:3.2.5-1.fc26.x86_64                          1/1 
    Running as unit: run-rca947160a2b2463aabd67ef848fe39c6.service
      Verifying        : postfix-2:3.2.5-1.fc26.x86_64                          1/1 

    Installed:
      postfix.x86_64 2:3.2.5-1.fc26                                                 

    Complete!

To configure it to accept the mails from `localhost` only, edit `/etc/postfix/main.cf` and add/change the following (leave the rest as default):

    myhostname = <your_hostname>
    mydomain = localhost  #or your domain if you have some configured on a system
    myorigin = $mydomain
    inet_interfaces = localhost
    inet_protocols = ipv4
    mynetworks = 127.0.0.0/8

For `<your hostname>`:

    $ hostname
    localhost.localdomain

Enable and start postfix:

    $ sudo systemctl enable postfix.service
    [sudo] password for [user]]: 
    Created symlink /etc/systemd/system/multi-user.target.wants/postfix.service → /usr/lib/systemd/system/postfix.service.
    $ sudo systemctl start postfix.service

Verify that it is up and listening

    $ netstat -lt | grep smtp
    tcp        0      0 localhost:smtp          0.0.0.0:*               LISTEN

Now you can send/receive local emails with mailx, mutter, evolution, and claws:

    Email Addresses: [user]@localhost
    Receiving Email Server Type: mbox spool file
    Spool File: /var/spool/mail/<user> 
    Sending Email Server Type: Sendmail

Running on `localhost`, changes to firewall are not necessary. 

