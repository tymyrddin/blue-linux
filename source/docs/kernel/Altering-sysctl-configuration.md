# Altering sysctl configuration

Using your favourite editor:

    $ sudo geany /etc/sysctl.conf

**Warning**: `systemd` only applies settings from `/etc/sysctl.d/*.conf` and `/usr/lib/sysctl.d/*.conf`. If you upgraded from Debian wheezy to jessie or stretch (or are on Ubuntu or Mint) and customised `/etc/sysctl.conf`, you need to rename it as `/etc/sysctl.d/99-sysctl.conf`. If you had something like `/etc/sysctl.d/foo`, you need to rename it to `/etc/sysctl.d/foo.conf`. 

    sudo geany /etc/sysctl.d/99-sysctl.conf

For now it is naught more than removing a few comment-out chars and adding a few lines: 

    #
    # /etc/sysctl.conf - Configuration file for setting system variables
    # See /etc/sysctl.d/ for additonal system variables
    # See sysctl.conf (5) for information.
    #

    #kernel.domainname = example.com

    # Uncomment the following to stop low-level messages on console
    #kernel.printk = 3 4 1 3

    ##############################################################3
    # Functions previously found in netbase
    #

Leave as is.
