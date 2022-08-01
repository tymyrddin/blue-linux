# Anonymise SSH sessions with Tor

In some countries, proving that you connected to a particular server is enough to be prosecuted, but SSH doesn't 
provide a native way to obfuscate to whom it connects. For that, [SSH](ssh.md) with [Tor proxy](tor-proxy.md) can be used.

## Configuration SSH

Install connect-proxy:

    $ apt-get install -y connect-proxy

### Set up OpenSSH to use Tor for a specific connection

Create or open `~/.ssh/config`

    $ vi ~/.ssh/config

Append the below entry (replacing mydomain.com with actual server domain name or IP and user with actual user):

```text
Host jumphost
HostName mydomain.com
User user
CheckHostIP no
Compression yes
Protocol 2
ProxyCommand connect -4 -S localhost:9050 $(tor-resolve %h localhost:9050) %p
```

### Set up OpenSSH to use Tor for a bunch of connections

```text
Host anonymous_*
CheckHostIP no
Compression yes
Protocol 2
ProxyCommand connect -4 -S localhost:9050 $(tor-resolve %h localhost:9050) %p
Host anonymous_mydomain
HostName mydomain.com
User user
Host anonymous_mydomain2
HostName mydomain2.com
User user
Port 980
```
