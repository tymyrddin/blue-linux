# SYN cookies

    # Uncomment the next line to enable TCP/IP SYN cookies
    # See http://lwn.net/Articles/277146/
    # Note: This may impact IPv6 TCP sessions too
    net.ipv4.tcp_syncookies=1

During a [SYN flood](attack-trees:docs/network/DoS)
 a server receives the first packet of the three-way TCP handshake and responds with a SYN-ACK but no further data is ever received from the initiating client.

A syncookie allows the server to defer using up any resources until the third packet in the three-way handshake has been received. At that time the peer's address has been mildly authenticated because the final packet in the handshake contains a reference to the sequence number that was sent by the server in the second packet. With this assurance, packet filters and resource quotas keyed to the peer's address will again be useful defences against resource attacks. 

The cookie mechanism is only implemented for IPv4. Glenn Griffin posted patches that add IPv6 support for syncookies. Andi Kleen, author of the original syncookie patch, wondered if the mechanism should be continued at all much less added to IPv6: //Syncookies are discouraged these days. They disable too many valuable TCP features (window scaling, SACK) and even without them the kernel is usually strong enough to defend against syn floods and systems have much more memory than they used to be. So I don't think it makes much sense to add more code to it, sorry.// 

Alternatively, you can set `net.ipv4.tcp_synack_retries = 2`.

