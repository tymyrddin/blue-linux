# Magic SysRq key

    ###################################################################
    # Magic system request Key
    # 0=disable, 1=enable all
    # Debian kernels have this set to 0 (disable the key)
    # See https://www.kernel.org/doc/Documentation/sysrq.txt
    # for what other values do
    kernel.sysrq=1

A kernel panic can happen, and sometimes this stops the X-server and you can't change to the console. What to do? Hitting the reset button and risk filesystem integrity?

NO! There is a possibility to shut down the system cleanly or find out the source of the kernel panic.
For this purpose there is a kernel option called "Magic SysRQ Key" in the section kernel hacking.
If this option is enabled you can use [a set of keyboard commands](https://www.linuxhowtos.org/Tips%20and%20Tricks/sysrq.htm).
