# Use a firewall as a VPN fail-safe mechanism

If you simply add a VPN using common instructions, it generally "fails open". That means, if the VPN breaks down, 
because the connection is interrupted, traffic will be sent without the VPN. It is much safer when it "fails closed", 
meaning that when the VPN connection breaks down, the whole internet connection must be down as long as the VPN 
connection is not restored. If your [chosen VPN](vpn.md) does not include being able to 
set a kill switch, you can use your firewall as a fail-safe mechanism:

1. Get the IP address of the VPN gateway that the kill switch is intended for using the `host` command.
2. Get the network interface name connected to your default gateway and the subnet of the local network using the 
`route` command.
3. Modify the `.ovpn` configuration file. Change the tun device to `-dev tun0` in the client configuration file. Then 
change the hostnames to IP addresses for the `-remote` option in the same configuration file.

## Kill switch using ufw

4. Make a shell script (killswitch-ufw.sh):

```text
ufw --force reset
ufw default deny incoming
ufw default deny outgoing
ufw allow in on tun0
ufw allow out on tun0
ufw allow in on [network interface name] from 192.168.0.0/24
ufw allow out on [network interface name] to 192.168.0.0/24
ufw allow out on [network interface name] to [IP address of the VPN gateway] port 1194 proto udp
ufw allow in on [network interface name] from [IP address of the VPN gateway] port 1194 proto udp
ufw enable
```

5. Make it executable:

```text
$ chmod +x killswitch-ufw.sh
```

6. Execute:

```text
$ ./killswitch-ufw.sh
```

## Kill switch using iptables

4. Make a shell script (killswitch-iptables.sh):

```text
iptables --flush
iptables --delete-chain
iptables -t nat --flush
iptables -t nat --delete-chain
iptables -P OUTPUT DROP
iptables -A INPUT -j ACCEPT -i lo
iptables -A OUTPUT -j ACCEPT -o lo
iptables -A INPUT --src 192.168.0.0/24 -j ACCEPT -i [network interface name]
iptables -A OUTPUT -d 192.168.0.0/24 -j ACCEPT -o [network interface name]
iptables -A OUTPUT -j ACCEPT -d [IP address of the VPN gateway] -o wlp6s0 -p udp -m udp --dport 1194
iptables -A INPUT -j ACCEPT -s [IP address of the VPN gateway] -i wlp6s0 -p udp -m udp --sport 1194
iptables -A INPUT -j ACCEPT -i tun0
iptables -A OUTPUT -j ACCEPT -o tun0
```

5. Make it executable:

```text
$ chmod +x killswitch-iptables.sh
```

6. Execute:

```text
$ ./killswitch-iptables.sh
```
    