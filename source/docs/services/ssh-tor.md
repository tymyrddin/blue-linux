# Anonymise SSH sessions with Tor

In some countries, proving that you connected to a particular server is enough to be prosecuted, but SSH doesn't 
provide a native way to obfuscate to whom it connects. For that, [SSH](ssh.md) with [Tor proxy](tor-proxy.md) can be used.

## Configuration ssh

Create or open `~/.ssh/config`

    $ vi ~/.ssh/config

Append the below entry (replacing XXX.XXX.XXX.XXX with actual server domain name or IP and user with actual user):

    Host jumphost
    HostName XXX.XXX.XXX.XXX
    User user
    CheckHostIP no
    Compression yes
    Protocol 2
    ProxyCommand connect -4 -S localhost:$orport $(tor-resolve %h localhost:$orport) %p