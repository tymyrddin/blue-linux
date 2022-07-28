# Make backups

Assume data loss is inevitable. It's not a matter of if, it is a matter of when. You best protect your data with a solid backup strategy.
* Make a backup of your entire system or synchronise files with a remote system 
* On Linux you can use [Rsync](http://rsync.samba.org/) (**r**emote **sync**) (GPL v3), an open source utility for fast 
incremental file transfer. It is a file-copying tool which can copy locally and to/from a remote host. It offers many 
options to control its behaviour, and its remote-update protocol can minimize network traffic to make transferring 
updates between machines fast and efficient. It is widely used for backups and mirroring and as an improved copy 
command for everyday use. The package provides both the `rsync` command line tool and optional daemon functionality. 
* If you make a backup of a system for the first time to be able to restore a system from (the whole point of it), test 
it with an actual restore. Having done so helps staying calm when the shit hits the fan.

## Installing rsync 

Installing it from the repository:

    $ sudo apt-get install rsync

## General rsync command

The general command is of the form:

    $ rsync [options] [source] [destination]

## Backup to external disk

`rsync`  uses an algorithm that minimises the amount of data copied by only moving the portions of files that have changed. It operates in a way similar to ssh, scp, and cp, for example:

    $ rsync -a [directoryname]/ /media/[path/to/external/disk]/[directoryname]

The `a` option is a combination flag. It stands for "archive" and syncs recursively (includes all subdirectories and subdirectories of subdirectories) and preserves symbolic links, [[en:linux:files|special and device files]], modification times, group, owner, and permissions.

There are a lot of different switches that you can use for `rsync` to personalize it to your specific needs, for example:

    -a means recursive (recurse into directories), links (copy symlinks as symlinks), perms (preserve permissions), times (preserve modification times), group (preserve group), owner (preserve owner), preserve device files, and preserve special files.
    -v means verbose and shows you what rsync is backing up.
    -z enables compression
    -h for human-readable, output numbers in a human-readable format
    -delete tells rsync to delete any files that are in the second directory that aren’t in the first directory. 

## Synchronize files from local to remote

While doing synchronization with a remote server, you need to specify `username` and `ip-address` of the remote server. 
You should also specify the destination directory on the remote server. The format is `username@machinename:path`.

    $ rsync -avz tymyrddin/ [username protected]@192.168.100.10:/home/tymyrddin/
    password:
    sending incremental file list
    ./
    modsecurity-2.9.2.tar.gz
    [snip]
    sent 4993369 bytes  received 91 bytes  2432411.23 bytes/sec
    total size is 4991313 speedup is 2.87

## Copy a remote directory to a local machine

In this example, a directory `/home/tymyrddin/pkgs` on a remote server is being copied in a local computer in 
`/tmp/mypkgs`.

    # rsync -avzh [username protected]:/home/tymyrddin/pkgs /tmp/mypkgs
    password:
    receiving incremental file list
    created directory /tmp/mypkgs
    pkgs/
    pkgs/lighttpd_1.4.45.orig.tar.xz
    [snip]
    sent 91 bytes  received 4.99M bytes  322.16K bytes/sec
    total size is 4.99M  speedup is 1.00

## Rsync over ssh

rsync allows you to specify the remote shell which you want to use. You can use `rsync ssh` to enable the secured remote connection.  To specify a protocol with rsync you need to give `-e` option with protocol name you want to use. Use `rsync -e ssh` to specify which remote shell to use. Example:

    # rsync -avzhe ssh [username protected]:/root/install.log /tmp/
    password:
    receiving incremental file list
    install.log
    sent 30 bytes  received 8.12K bytes  1.48K bytes/sec
    total size is 30.74K  speedup is 3.77

## Do not overwrite modified files at the destination

In a typical sync situation, if a file is modified at the destination, we might not want to overwrite the file with the 
old file from the source. Use the `-u` option.
