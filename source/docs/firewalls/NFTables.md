# NFTables

The successor of iptables. So let me try. Still at it and //Warning: Not been tested yet//.
 
## Basic idea 

    flush ruleset

    table inet filter {

        set tcp_accept {
            type inet_service; flags interval;
            
            elements = { http, https, ssh,
            }
        }
        
        set udp_accept {
            type inet_service; flags interval;
            
            elements = { openvpn,
            }
        }

        chain base_checks {
            # allow established/related connections
            ct state {established, related} accept
            # early drop of invalid connections
            ct state invalid drop
        }
        
        chain input {
            type filter hook input priority 0; policy drop;

            # Accept on localhost
            iifname lo accept
            jump base_checks
            
            # Accept ICMPv6
            meta l4proto ipv6-icmp icmpv6 type { destination-unreachable, packet-too-big, \
            time-exceeded, parameter-problem, mld-listener-query, mld-listener-report, \
            mld-listener-reduction, nd-router-solicit, nd-router-advert, nd-neighbor-solicit, \
            nd-neighbor-advert, ind-neighbor-solicit, ind-neighbor-advert, mld2-listener-report \
            } accept
            
            # Accept ICMP
            meta l4proto icmp icmp type { destination-unreachable, router-solicitation, \
            router-advertisement, time-exceeded, parameter-problem } accept
            
            # Accept mDNS
            udp dport mdns ip6 daddr ff02::fb accept
            udp dport mdns ip daddr 224.0.0.251 accept
            
            # Accept UPnP IGD port mapping reply
            udp sport 1900 udp dport >= 1024 ip6 saddr { fd00::/8, fe80::/10 } meta \
            pkttype unicast limit rate 4/second burst 20 packets accept
            udp sport 1900 udp dport >= 1024 ip saddr { 10.0.0.0/8, 172.16.0.0/12, \
            192.168.0.0/16, 169.254.0.0/16 } meta pkttype unicast limit rate 4/second \
            burst 20 packets accept 
            
            # Allow ports
            tcp dport @tcp_accept accept
            udp dport @udp_accept accept
        }
        
        # Not a gateway. We do not forward. 
        chain forward {
            type filter hook forward priority 0; policy drop;
            jump base_checks
        }
        
        # Chain to accept all outgoing packets
        chain output {
            type filter hook output priority 0; policy accept;
            
        }
        
    }
