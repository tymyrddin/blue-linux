# Disabling startup applications

For example, do you really need Samba for sharing files over the network, or the Bluetooth service to connect to 
Bluetooth devices on a computer that doesn't have a Bluetooth adapter? 

* Go to /System -> Preferences -> Startup Applications (Debian and its derivatives)
* Remove check marks next to the services you wish to disable at startup. 

Be careful turning off services. Some other applications might stop functioning because they depend on a disabled 
service. Try one by one.


