# Blacklist firewire and thunderbolt

A direct memory access (DMA) attack is a type of side channel attack in which an adversary penetrates a device by 
exploiting the presence of high-speed expansion ports that permit Direct Memory Access. Firewire, thunderbolt and 
ExpressCard allow (by design) any connecting device full direct memory access to your system. They can be disabled 
in `/etc/modprobe.d/blacklist-dma.conf` (in debian):

    blacklist firewire-core
    blacklist thunderbolt

The modules will be blacklisted upon reboot.

