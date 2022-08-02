# Renew IP lease 

A DHCP client can on occasion send information in DHCP requests: hostname, MAC address, operating system, and DHCP 
version. All operating systems provide their most recent IP address to the DHCP server. 
If you [change your MAC address](change-mac.md) to minimise risk, best to also renew the IP leases on the 
router.

There are several ways to renew the IP lease, by using command line tools such as `nmcli` or `dhclient`, or by restarting network services.

Restarting network service (Debian-based):

```
$ sudo /etc/init.d/networking restart
```

On the command-line with `dhclient` (The `-r` flag explicitly releases the current lease, and once released, the client exits):

```
$ sudo dhclient -r
```

Now a fresh IP can be obtained:

```
$ sudo dhclient
```

On the command-line with `nmcli`:

```
$ nmcli con
```

From the list that appears, get the NAME of the connection you wish to request a new lease for, then bring down and up:

```
$ nmcli con down id 'NAME'
$ nmcli con up id 'NAME'
```
