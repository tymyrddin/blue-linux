# Protected links

    ###################################################################
    # Protected links
    #
    # Protects against creating or following links under certain conditions
    # Debian kernels have both set to 1 (restricted) 
    # See https://www.kernel.org/doc/Documentation/sysctl/fs.txt
    #fs.protected_hardlinks=1
    #fs.protected_symlinks=1

On systems that have user-writable directories on the same partition as system files, [a long-standing class of security issues](https://www.kernel.org/doc/html/latest/admin-guide/sysctl/fs.html#protected_hardlinks) is the hardlink-based time-of-check-time-of-use race, most commonly seen in world-writable directories like `/tmp`. The common method of exploitation of this flaw is to cross privilege boundaries when following a given hardlink (i.e. a root process follows a hardlink created by another user). Additionally, an issue exists where users can "pin" a potentially vulnerable `setuid`/`setgid` file so that an administrator will not actually upgrade a system fully.

The solution is to permit hardlinks to only be created when the user is already the existing file's owner, or if they already have read/write access to the existing file. Both are set to 1 by default, but if you wish to turn it off, this is where you could.
