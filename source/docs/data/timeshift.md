# Shift back and forth in time from past to present

Assume data loss is inevitable. It's not a matter of if, it is a matter of when. You best protect your data with a solid backup strategy.
 
* Make an `rsync` Timeshift backup of your entire system, or synchronise files with a remote system using `rsync`. 
* [Rsync](http://rsync.samba.org/) (**r**emote **sync**) (GPL v3) is an open source utility for fast 
incremental file transfer. It is a file-copying tool which can copy locally and to/from a remote host. It offers many 
options to control its behaviour, and its remote-update protocol can minimize network traffic to make transferring 
updates between machines fast and efficient. It is widely used for backups and mirroring and as an improved copy 
command for everyday use. The package provides both the `rsync` command line tool and optional daemon functionality. 
* If you make a backup of a system for the first time to be able to restore a system from (the whole point of it), test 
it with an actual restore. Having done so helps keep calm when the bleep hits the fan.

## Rsync

### Installing rsync 

Installing it from the repository:

    $ sudo apt-get install rsync

### General usage

The general command is of the form:

    $ rsync [options] [source] [destination]

Backup to external disk

`rsync`  uses an algorithm that minimises the amount of data copied by only moving the portions of files that have changed. It operates in a way similar to ssh, scp, and cp, for example:

    $ rsync -a [directoryname]/ /media/[path/to/external/disk]/[directoryname]

The `a` option is a combination flag. It stands for "archive" and syncs recursively (includes all subdirectories and subdirectories of subdirectories) and preserves symbolic links, [[en:linux:files|special and device files]], modification times, group, owner, and permissions.

There are a lot of different switches that you can use for `rsync` to personalize it to your specific needs, for example:

    -a means recursive (recurse into directories), links (copy symlinks as symlinks), perms (preserve permissions), times (preserve modification times), group (preserve group), owner (preserve owner), preserve device files, and preserve special files.
    -v means verbose and shows you what rsync is backing up.
    -z enables compression
    -h for human-readable, output numbers in a human-readable format
    -delete tells rsync to delete any files that are in the second directory that aren’t in the first directory. 

### Synchronize files from local to remote

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

### Copy a remote directory to a local machine

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

### Rsync over ssh

rsync allows you to specify the remote shell which you want to use. You can use `rsync ssh` to enable the secured remote connection.  To specify a protocol with rsync you need to give `-e` option with protocol name you want to use. Use `rsync -e ssh` to specify which remote shell to use. Example:

    # rsync -avzhe ssh [username protected]:/root/install.log /tmp/
    password:
    receiving incremental file list
    install.log
    sent 30 bytes  received 8.12K bytes  1.48K bytes/sec
    total size is 30.74K  speedup is 3.77

### Do not overwrite modified files at the destination

In a typical sync situation, if a file is modified at the destination, we might not want to overwrite the file with the 
old file from the source. Use the `-u` option.

## Timeshift

Timeshift is free and open source software (source code can be found on GitHub) released under the LGPL-3.0 and GPL-3 
licenses. The application is available in the official repositories of the major Linux distributions.

To install on Debian/Ubuntu:

    sudo apt install timeshift

Timeshift can be launched from the desktop environment application menu, or from the command line. 

* The first time the application runs, choose what kind of backend to use, rsync or btrfs.
  * Btrsf-based snapshots are byte-for-byte copies of the original filesystem, and are created and restored in no time by 
  using the native snapshot feature of the btrsf filesystem. They cannot be saved on external disks or devices. If the 
  main disk fails, so does the snapshot.
  * Rsync-based snapshots are based on the use of hard links, implementing an incremental strategy. The first backup is a 
  full backup; subsequent backups will include only changed files. Snapshots created by rsync can be copied on external 
  devices formatted with a Linux filesystem. 
* Choose weekly, daily, hourly, on boot, and how many snapshots should be kept. Snapshots can also be created on demand.
* Choose whether and which users home directories should be included in the snapshots and what kind of files should be 
included (hidden ones or all).

The snapshot will be kept inside the `/timeshift` directory on the selected filesystem.

To explore the files included in the snapshot, select it in the list and click on the Browse button. A file manager 
window will be opened displaying the included files. In the same way, delete a snapshot by clicking on the Delete 
button and restore a snapshot by clicking on Restore. If no changes to system partitions were made, nothing needs to be 
modified.


