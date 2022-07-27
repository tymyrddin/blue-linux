# Service management

Be careful disabling/stopping services. Some other applications might stop functioning because they depend on a disabled 
service. Try one by one.

Most recent distributions use the [Systemd](https://en.wikipedia.org/wiki/Systemd) system manager. Some still use the 
old SysVinit system manager.

The easiest way to discover which system manager is in use, is by using the use the `pstree` command and to check the 
first process ever run on your system:

```text
$ pstree | head -n 5
systemd-+-ModemManager---2*[{ModemManager}]
    |-NetworkManager---2*[{NetworkManager}]
    |-accounts-daemon---2*[{accounts-daemon}]
    |-acpid
    |-apache2-+-2*[apache2---26*[{apache2}]]
```

## Getting a list of services

To list services on Linux, when you are on a systemd system:

    $ systemctl list-units --type=service

This command will show you only the services that are active or the services that have failed (in red) on the system.

List all services:

    $ systemctl list-units --type=service --all

Only loaded services are listed. On boot, systemd loads unit files and it may choose not to load a specific service if 
it finds that it won’t be used by the system.

List services by state (active, inactive, activating, deactivating, failed, not-found or dead):

    $ systemctl list-units --state=<state1>,<state2>

In order to list all service files available, use `list-unit-files`:

    $ systemctl list-unit-files --type=service

## Status of a service
To verify whether a service is active or not, run this command (for example, for apache2):

    $ sudo systemctl status apache2

## Managing services
To start/stop/restart a service in Linux:

    $ sudo systemctl start <service>
    $ sudo systemctl stop <service>
    $ sudo systemctl restart <service>

To force the service to reload its configuration files:

    $ sudo systemctl reload <service>

Enable/disable a service at boot:

    $ sudo systemctl enable <service>
    $ sudo systemctl disable <service>

 