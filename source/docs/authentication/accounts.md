# Disable and enable user accounts

## Shadow file modification

The easiest way to disable a user account is to modify the `/etc/shadow` file, which holds encrypted passwords for 
users listed in `/etc/passwd`. An example user entry found in the `/etc/shadow` file:

    tester:$6dKR$Yku3LWgJmomsynpcle9BCA:15711:0:99999:7:::

To disable this account add `*` or `!` in front of the encrypted password:

    tester:!$6dKR$Yku3LWgJmomsynpcle9BCA:15711:0:99999:7:::

This can also be achieved by:

    # usermod -L tester

Any login method, which uses the `/etc/shadow` file to authenticate a user, will no longer be able to decrypt the 
user's password and will not allow him/her to login:

    $ su tester
    Password: 
    su: Authentication failure

To enable the user account simply remove the added magic from the `/etc/shadow` file or use the usermod command:

    # usermod -U tester

This method of disabling user accounts in the Linux system is only valid for programs or commands, which use the 
`/etc/shadow` file to authenticate users. If a user has already exchanged ssh keys he/she will still be able to log in 
despite such modifications.

## nologin User Shell

A more secure way of disabling a user account is to replace the existing user login shell with a pseudo shell such as 
`/usr/sbin/nologin`. `nologin` will display a message:

    This account is currently not available.

To do this, modify the `/etc/password` file and change the user's entry from:

    tester:x:1001:1001:Tester,User,,:/home/tester:/bin/bash

to:

    tester:x:1001:1001:Tester,User,,:/home/tester:/usr/sbin/nologin

User tester will no longer be able to log in with a valid password:

    $ su tester
    Password: 
    This account is currently not available.