# ICMP redirects

    ###################################################################
    # Additional settings - these settings can improve the network
    # security of the host and prevent against some network attacks
    # including spoofing attacks and man in the middle attacks through
    # redirection. Some network environments, however, require that these
    # settings are disabled so review and enable them as needed.
    #
    # Do not accept ICMP redirects (prevent MITM attacks)
    net.ipv4.conf.all.accept_redirects = 0
    net.ipv4.conf.default.accept_redirects = 0
    net.ipv6.conf.all.accept_redirects = 0
    # _or_
    # Accept ICMP redirects only for gateways listed in our default
    # gateway list (enabled by default)
    # net.ipv4.conf.all.secure_redirects = 1
    #
    # Do not send ICMP redirects (we are not a router)
    net.ipv4.conf.all.send_redirects = 0

There are certain cases where ICMP packets can be used to attack a network. Although this type of problem is not common anymore, there are situations where such problems do happen. This is the case with ICMP redirect, or ICMP Type 5 packet. ICMP redirects are used by routers to specify better routing paths out of one network, based on the host choice, so basically it affects the way packets are routed and destinations.

Through ICMP redirects, a host can find out which networks can be accessed from within the local network, and which are the routers to be used for each such network. The security problem comes from the fact that ICMP packets, including ICMP redirect, are extremely easy to fake and basically it would be rather easy for an attacker to forge ICMP redirect packets.

The adversary can then on basically alter your host's routing tables and divert traffic towards external hosts on a path of his/her choice; the new path is kept active by the router for 10 minutes. Due to this fact and the security risks involved in such scenario, it is still a recommended practice to disable ICMP redirect messages (ignore them) from all public interfaces.
