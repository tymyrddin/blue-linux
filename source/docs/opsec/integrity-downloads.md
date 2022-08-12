# Check integrity of downloads

When downloading an ISO image of, for example, the latest Linux distro, installing or upgrading packages, or 
downloading software, you can verify the files have downloaded correctly and securely by using checksums. 
Checksums ensure the integrity of data portions for data transmission or storage. Checksums is a simple error-detection 
scheme in which each transmitted message is accompanied by a numerical value based on the number of set bits in the 
message. The receiving station then applies the same formula to the message and checks to make sure the accompanying 
numerical value is the same. If not, the receiver can assume that the message has been garbled (or was altered).

## Verifying downloaded software

When downloading software (`.iso`s and `.deb`s and the like), also download the `xxxsum` (choose from what is available) 
and check the integrity (it is the intended file, and nothing has changed underway). 

For example do:

    $ sha256sum some-file.iso

and compare the output from the command with the key listed in the associated `sha256` file.

## Troubleshooting unauthenticated packages

Integrity checks are integrated in linux package managers. Never ever continue with installation if you get a:

    WARNING: The following packages cannot be authenticated!

0. It may be that your system is set to use a proxy server for a network you are not connected to. Set your Network Proxy method to None and Apply System Wide, and check if that helped.

1. Check repositories are not corrupted in `/etc/apt/sources.list`. If so, repair with correct repositories and try again.

2. Check GPG keys (apt-key)

```
# apt-key list 
```

3. Update the local keyring with the keyring of archive keys and remove from the keyring the archive keys which are no longer valid:

```
# apt-key update
# apt-get update
```

4. If still not works, reinstall the archive-keyring.

```
# aptitude reinstall [distro]-archive-keyring
```

For example:

```
Kali Keyring – kali-archive-keyring
Debian Keyring – debian-archive-keyring
Ubuntu Keyring – ubuntu-archive-keyring
```

5. Still not works? Hit the forums.

