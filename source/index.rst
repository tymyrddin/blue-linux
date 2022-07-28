GNU/Linux mitigations
================================================

"Linux" is really GNU software operating with a Linux kernel, and GNU software there are many resulting in an
`incredible amount of distributions <https://distrowatch.com/>`_, all called "Linux". Some even build on each other, such as Debian -> Ubuntu.
It is impossible to cover them all. These mitigations are kept as simple as possible, with tools found in most
distros. Some things are harder to cover. For example, each distro has its own privacy settings somewhere, and
there are even distro's that have specialised in privacy.

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

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Data

   docs/data/README.md
   docs/data/removable-media.md
   docs/data/archive-compress.md
   docs/data/backups.md
   docs/data/disk-encryption.md
   docs/data/file-encryption.md
   docs/data/shred-and-delete.md

.. toctree::
   :glob:
   :maxdepth: 1
   :includehidden:
   :caption: Privacy

   docs/privacy/README.md
   docs/privacy/*

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
   :caption: Social engineering

   docs/social-engineering/README.md
   docs/social-engineering/browsers.md
   docs/social-engineering/check-mail.md

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