# Change MAC address

A MAC address identifies the device connected to a network and allows the network to track, restrict or allow access 
based on it. Routers identify and assign static IP addresses based on the MAC addresses of devices. Before you try to 
change the MAC address, you need to know the value that you want to use.

Set the 2's place bit (the "locally administered" bit) in the first byte, to differentiate it from a guaranteed 
globally unique MAC address. Usually the first three bytes an unicast MAC address is an 
"Organizationally Unique Identifier" (OUI) that the IEEE assigned to the manufacturer of your Ethernet device. 
Manufacturers are required to make sure they keep the last 3 bytes unique. 

Avoiding all of that knowledge, the [MAC address generator tool](https://miniwebtool.com/mac-address-generator/) can 
generate a valid address for you.

With 'macchanger' you can change the MAC address of any Ethernet network device:

Turn off your network interface:

```
$ sudo ifconfig eth0 down
```

Use 'macchanger' to randomly generate new MAC address and assign it to `eth0` network interface:

```
$ sudo macchanger -r eth0
Current MAC: 00:10:4C:25:7A:3F (unknown)
Faked MAC:   32:cf:cb:6c:63:cd (unknown)
```

Enable `eth0` network interface and check new MAC address:

```
$ sudo ifconfig eth0 up
$ sudo ifconfig eth0
```

If a specific MAC address, like `00:0a:95:9d:68:16`, is required:

```
$ sudo macchanger -m 00:0a:95:9d:68:16 eth0
```
