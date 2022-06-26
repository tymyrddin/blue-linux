# Spoof protection

    # Uncomment the next two lines to enable Spoof protection (reverse-path filter)
    # Turn on Source Address Verification in all interfaces to
    # prevent some spoofing attacks
    net.ipv4.conf.default.rp_filter=1
    net.ipv4.conf.all.rp_filter=1

Reverse path filtering is a mechanism adopted by the Linux kernel, as well as most of the networking devices, to check whether a receiving packet source address is routable.

When a machine with reverse path filtering enabled receives a packet, the machine will first check whether the source of the received packet is reachable through the interface it came in.

* If it is routable through the interface which it came, then the machine will accept the packet
* If it is not routable through the interface, which it came, then the machine will drop that packet.

