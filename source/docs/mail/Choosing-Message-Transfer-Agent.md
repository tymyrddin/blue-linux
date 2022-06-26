# Choosing a Message Transfer Agent

  * [Exim](https://www.exim.org/) uses the Sendmail design model where a single binary controls all the facilities of the MTA. This monolithic design is inherently less secure due to the lack of binary separation between the individual components of the system. Exim separates processes and has well-defined stages where it gains or loses privileges. Debian with MATE comes with the exim mailserver installed.
  * [Postfix](http://www.postfix.org/|Postfix) has a modular design to improve security over Qmail. A master daemon (a background process) launches other smaller processes with limited privileges that do specific tasks related to the various stages of mail delivery. The modular approach limits the effects of attacks.
  * [Sendmail](https://www.proofpoint.com/us/sendmail-open-source) is the default MTA shipped with many Linux distributions and is the most well-known. It is easy to configure but had the most security loopholes, partly because it was designed long before hackers started attacking email systems. Developers fix most security issues quickly, but because it has the most number of users, it is still the biggest target for hackers.

If you install the one, the other is uninstalled. 

