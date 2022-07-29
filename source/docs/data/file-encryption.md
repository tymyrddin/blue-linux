# File encryption 

Filesystem level encryption, often called file/folder encryption or stacked level encryption, is a form of disk 
encryption where individual files or directories are encrypted by the file system itself. This is in contrast to full 
disk or block level device encryption where an entire partition or disk, in which the file system resides, is encrypted.

## EncFS

[EncFS](https://vgough.github.io/encfs/) provides an encrypted filesystem in user-space. It runs without any special 
permissions and uses the FUSE library and Linux kernel module to provide the filesystem interface. EncFS is open source 
software, licensed under the GPL.

## eCryptfs

[eCryptfs](http://ecryptfs.org/) stores cryptographic meta data in the header of each file written, so that encrypted 
files can be copied between hosts; the file will be decrypted with the proper key in the Linux kernel keyring. The 
eCryptfs kernel module is available in all Linux kernels since 2006. The eCryptfs user space utilities 
(`ecryptfs-utils`) are available in all major Linux distributions.

## VeraCrypt

[VeraCrypt](https://www.veracrypt.fr/en/Home.html) is a fork of the discontinued TrueCrypt project. It is a free and 
open-source utility for on-the-fly encryption (OTFE). The software can create a virtual encrypted disk that works just 
like a regular disk but within a file. It can also encrypt a partition or (in Windows) the entire storage device with 
pre-boot authentication.



