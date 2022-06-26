# Single Ring Recovery

    #
    # Do not accept IP source route packets (we are not a router)
    net.ipv4.conf.all.accept_source_route = 0
    net.ipv4.conf.default.accept_source_route = 0
    net.ipv6.conf.all.accept_source_route = 0
    #

Accept packets with SRR option? Not on a PC. Whether to accept packets with SRR option is typically enabled on routers.

