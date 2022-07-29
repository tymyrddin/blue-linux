# Use a password manager

The majority of people use very weak passwords and reuse them on different websites. How are you supposed to use strong, 
unique passwords on all the websites you use? The solution is a password manager.

Password managers store your login information for all the websites you use and help you log into them automatically. 
They encrypt your password database with a master password — the master password is the only one you have to remember.

## Managers

* [Dashlane](https://www.dashlane.com/)
* [1Password](https://1password.com/)
* [Bitwarden](https://bitwarden.com/)

## It does not protect from keyloggers

Most password manager work by copy-pasting data quickly from your manager to the field (on the website) or by simulating 
keystrokes for all the data on file.

A keylogger captures keystrokes and would capture all passwords entered by a password manager that simulated keystrokes. 
Nearly all keyloggers even include the capability to take screenshots at particular intervals of time and save all the 
contents of the clipboard to a file. The last bit is important, because it sort of renders even password managers that 
use the clipboard to fill in these forms useless.

The real solution to preventing these attacks is to [monitor your system](../malware/README.md) for any keyloggers and 
use an [AV solution](../malware/clean-machine.md).