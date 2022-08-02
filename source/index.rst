GNU/Linux mitigations
================================================

"Linux" is really GNU software operating with a Linux kernel, and GNU software there are many resulting in an
`incredible amount of distributions <https://distrowatch.com/>`_, all called "Linux". Some even build on each other, such as Debian -> Ubuntu.
It is impossible to cover them all.

Version 0.1: These mitigations are kept as simple as possible, with tools found in most distros. Some things are harder
to cover. For example, each distro has its own privacy settings somewhere, and there are even distro's that have
specialised in privacy.

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Accounts and authentication

   docs/authentication/README.md
   docs/authentication/accounts.md
   docs/authentication/passwords.md
   docs/authentication/password-manager.md
   docs/authentication/resuming.md
   docs/authentication/mfa.md
   docs/authentication/ssh-mfa.md
   docs/authentication/sudo-killers.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Services and applications

   docs/services/README.md
   docs/services/service-management.md
   docs/services/apparmor.md
   docs/services/restrict-access.md
   docs/services/startup-applications.md
   docs/services/browsers.md
   docs/services/messaging.md
   docs/services/email-services.md
   docs/services/ssh.md
   docs/services/vpn.md
   docs/services/vpn-fail-open.md
   docs/services/dns-servers.md
   docs/services/tor-proxy.md
   docs/services/ssh-tor.md
   docs/services/change-mac.md
   docs/services/renew-lease.md
   docs/services/edit-hosts-file.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Data

   docs/data/README.md
   docs/data/removable-media.md
   docs/data/archive-compress.md
   docs/data/timeshift.md
   docs/data/disk-encryption.md
   docs/data/file-encryption.md
   docs/data/shred-and-delete.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Privacy

   docs/privacy/README.md
   docs/privacy/devices.md
   docs/privacy/metadata.md
   docs/privacy/metadata-images.md
   docs/privacy/hexeditors.md
   docs/privacy/bleachbit.md
   docs/privacy/mat2.md
   docs/privacy/privacy-distros.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Malware

   docs/malware/README.md
   docs/malware/clean-machine.md
   docs/malware/analysing-trojans.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Operations security

   docs/opsec/README.md
   docs/opsec/email-use.md
   docs/opsec/check-mail.md
   docs/opsec/browsing.md
   docs/opsec/integrity-downloads.md
   docs/opsec/*

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Guards! Guards!

   docs/guards/README.md
   docs/guards/soup.md
   docs/guards/netfilter-and-iptables.md
   docs/guards/nftables.md
   docs/guards/gufw-and-ufw.md
   docs/guards/ids.md
   docs/guards/*

.. toctree::
   :caption: Links

   All mitigations <https://tymyrddin.github.io/mitigations/>