# Archiving and compressing

Linux offers separate tools for gathering groups of files into a single archive and compressing that archive for 
efficient storage. Oh yuk, "efficient", oh well. It's about using less disk space and reducing transfer times over 
networks. And comes at a price. It can increase your CPU usage. 

## tar

You can combine archiving and compressing together by using additional options to the `tar` (**t**ape **ar**chiver) 
command. Tar can behave differently on different distros. The manual page contains descriptions of the myriad of 
features that come with `tar`. The basic operations of `tar`:

*  Create a backup archive: `c`
*  Extract files from an archive: `x`
*  Compare differences between archives: `d`
*  Update files in an archive: `u`
*  Append files: `r` or `A`
*  Delete files from an existing archive: `d`
*  List contents of an archive: `t`

When creating a `tar` archive, you can add options that compress the resulting archive. With `j` the archive will be 
compressed in bzip2 format, and with `z` in gzip format. For example, tar with `bzip2` compression:
    
    $ tar xjvf funnybusiness.tar.bz2 *.txt

You can also use other compression mechanisms like `lzop` with tar. It is faster, but the compression is less than 
with `bzip2` which is around 10 times slower while only giving twice the amount of compression. You can also set the 
compression level in the compression commands themselves.

## gzip

`gzip` compresses the size of the given files using Lempel-Ziv coding (LZ77). Whenever possible, each file is replaced 
by one with the extension .gz.

Compress a file:

    $ gzip funnybusiness.txt

Compress all images with a `.jpg` extension in a directory:

    $ gzip *.jpg

Compress all files in a directory:

    $ gzip -rv [directory]

Test integrity of a `gzip` compressed file:

    $ gzip -tv funnybusiness.gz

To uncompress a compressed file:

    $ gunzip -v funnybusiness.gz

Fastest compression time, least compression:

    $ gzip -1 funnybusiness.gz

Slowest compression time, most compression:

    $ gzip -9 funnybusiness.gz

## bzip2

`bzip2` compresses files using the Burrows-Wheeler block sorting text compression algorithm and Huffman coding. 
Compression is generally considerably better than that achieved by bzip command (LZ77/LZ78-based compressors). Whenever 
possible, each file is replaced by one with the extension `.bz2`.

    $ bzip2 [filename]

Uncompress:

    $ bunzip [filename].bz2

## lzop

`lzop` uses the LZO data compression library for compression services, and its main advantages over gzip are much 
higher compression and decompression speed (at the cost of some compression ratio). [lzop](http://www.lzop.org/) is 
copyrighted under the terms of the GNU General Public License (GPL). 

You will probably have to install it first:

    $ sudo apt-get install lzop

Compress:

    $ lzop [filename]

Unlike `gzip` and `bzip2`, `lzop` has no separate command for unlzopping. NO UNLZOPPING! Use the `d` option:

    $ lzop -dv [filename].lzo

