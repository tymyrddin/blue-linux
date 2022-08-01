# Use a firewall as a VPN fail-safe mechanism

If you simply add a VPN using common instructions, it generally "fails open". That means, if the VPN breaks down, 
because the connection is interrupted, traffic will be sent without the VPN. It is much safer when it "fails closed", 
meaning that when the VPN connection breaks down, the whole internet connection must be down as long as the VPN 
connection is not restored. If your [chosen VPN](vpn.md) does not include being able to 
set a kill switch, you can use your firewall as a fail-safe mechanism:

As an example, with `ufw`. 

Set all traffic to deny if you haven't already:

    $ sudo ufw default deny outgoing
    $ sudo ufw default deny incoming

Permit OpenVPN traffic (if using OpenVPN adapter is probably tun0 but check.)

    $ sudo ufw allow out on tun0 from any to any

For added security you may want to keep incoming traffic disabled but if desired or required then allow it:

    $ sudo ufw allow in on tun0 from any to any

With this rule all non VPN traffic (and subsequently DNS requests not routed though VPN) will be blocked.

But, this set up requires that you disable the firewall to connect to the VPN and then enable it once connection is made. To allow establishment of a connection to the VPN server even when the firewall is enabled:

    $ sudo ufw allow out from any to [VPN server IP address]

Add multiple rules for all VPN servers you will be using. If you want more strict rules and better security than only 
allow desired ports on tun0.