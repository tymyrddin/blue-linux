# Turn on/off camera/webcam 

Adversaries can try to gain access with remote-access Trojans (RATs) – malware that gives the adversary administrative control over its targeted computers, including, in this case, the ability to remotely control webcams. It is an invisibly-installed malware program spread via email attachment or by [tricking victims into visiting a malicious site](attack-trees:docs/social-engineering/Phishing).

Tape the camera. It may even be possible to turn it off in BIOS (depending on your version). Better yet, if you know what driver module is controlling the webcam, you can disable the driver with `modprobe -r`.

Check with:
    
    $ lsmod | grep "uvc"

If stuff like this appears, your webcam device uses an [uvc driver](https://www.ideasonboard.org/uvc/):

    uvcvideo               79005  0 
    videobuf2_vmalloc      12816  1 uvcvideo
    videobuf2_core         47787  1 uvcvideo
    videodev              126451  3 uvcvideo,v4l2_common,videobuf2_core
    media                  18305  2 uvcvideo,videodev
    usbcore               195340  7 uvcvideo,ums_realtek,usb_storage,ehci_hcd,ehci_pci,usbhid,xhci_hcd

To disable the cam:

    $ sudo modprobe -r uvcvideo 

To enable the cam:

    $ sudo modprobe uvcvideo

If not an uvcvideo driver, try `$ sudo lsmod | grep "media"` and use the `modinfo` command to find out more about the modules listed behind it to locate your webcam driver module:

    $ sudo modinfo [modulename] 

Then replace the `uvcvideo` in the above `modprobe` command with the name of your driver module.

To disable the webcam at boot (if file not exists, create it, use your preferred editor):

    $ sudo geany /etc/modprobe.d/blacklist.conf

At bottom of the file add this line: `blacklist uvcvideo` (or the name of your driver instead of uvcvideo).

Save the file and reboot. Your webcam is no longer functioning.

