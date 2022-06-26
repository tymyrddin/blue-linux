# Logging

    # Log Martian Packets
    net.ipv4.conf.all.log_martians = 1
    net.ipv4.conf.default.log_martians = 1
    net.ipv4.conf.default.accept_source_route = 0
    net.ipv4.conf.default.accept_redirects = 0
    net.ipv4.conf.default.secure_redirects = 0

Log packets with impossible addresses to kernel log.

