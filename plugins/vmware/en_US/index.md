# Vmware

## Presentation

The purpose of this plugin is to be able to obtain information from your Vmware platform(s) and to be able to perform some actions on your VMs if necessary.

The plugin does not contain any dependencies. VM control will be done via SSH.

![introduction01](../../images/vmware/vmware_icon.png)


## Prerequisites

The only prerequisite is:
* Allow SSH access on your ESXi server(s)


## Configuration

### General configuration

There is no particular parameter in the plugin configuration.

### Add an ESXi server type equipment

* Click the Add button on the Vmware plugin page
* Enter the name of your equipment
* Click OK

On the ESXi equipment page you will need to enter the following information:

* ESXi host's IP Address
* Login (You can create a dedicated account for this need by limiting the rights of this account if you wish)
* Password
* Save ESXi equipment


## Informations

When saving the ESXi, the ESXi is not queried directly.

> You must use the synchronize button or the Refresh command to start querying the ESXi and retrieve information from the ESXI and its VMs. This takes a few tens of seconds depending on the amount of configured VMs (Noted between 10 seconds for 5 Vms and 180 seconds for 50 Vms).

Each VM will have the following informations :
* Number of snapshots
* List of snapshots
* Vmware Tools Status : Started ![introduction01](../../images/vmware/coche_verte.png) / Not Started ![introduction01](../../images/vmware/coche_orange.png) / OutDated ![introduction01](../../images/vmware/roue_crantee_orange.png) / Not Installed ![introduction01](../../images/vmware/croix_rouge.png)
* VM status : Online ![introduction01](../../images/vmware/coche_verte.png) / Offline ![introduction01](../../images/vmware/croix_rouge.png)
* Operating system
* Total RAM amount
* Number of CPUs
* Number of cores per CPU
* Uptime in seconds (0 if offline)
* Uptime of the VM, not the OS, displayed in the format Years / Months / Days / Hours / Minutes / Seconds
* CPU usage (MHz) allows to follow via cron5 the CPU usage of each VMs
* Memory usage (GB) allows to follow via cron5 the memory usage of each VMs


Each VM will have the following commands :
* Reboot OS -> VMWARE Equivalent : Restart - Vmware Tools Required
* Reboot Hard -> VMWARE Equivalent : Reset
* Stop OS -> VMWARE equivalent : ShutDown - Vmware Tools required
* Stop Hard -> VMWARE Equivalent : PowerOff
* Power On ->; VMWARE Equivalent : PowerOn
* Take a snapshot -> More details below on command options
* Delete a snapshot -> More details below on command options

An ESXi will have the following informations :
* Number of VMs
* List of VMs
* Updated version of ESXi available? (Update once a day via CronDaily)
* Operating system
* Total RAM amount
* Number of CPUs
* Number of cores per CPU
* Uptime in seconds
* Uptime displayed in Years / Months / Days / Hours / Minutes / Seconds format
* Processor usage (MHz) allows to follow via cron5 the CPU usage of the server
* Memory usage (GB) allows to follow via cron5 the Memory usage of the server


## Take a snapshot command parameters :

The Name - Description field takes the following parameters - **No space in the Description field** :
* Name = NameOf YourSnapshot Description = Description_Of_Your_Snapshot


If you want to use spaces in the name or description, enter the information like this :
* Name = "Name of your snapshot" Description = "Description of your snapshot"

> **Attention** to respect capitals for Name and Description as well as the space before Description.


The Memory field allows you to say if you want to have the memory state of the VM during the snapshot, it takes the following parameter :
* NON
* OUI

## Delete snapshot command parameter :
The Snap Name field is to be filled in as follows :
* Name=NomDeVotreSnapshot

If you have spaces in the name of the snapshot it can be as follows :
* Name = "Name of your snapshot"

## Scenario idea

##### Scenario 1
Send an alert on the number of snapshot associated with a VM -> Too many snapshots that is not good

##### Scenario 2
Send an alert about snapshot presence in a VM since XX days -> Keeping a snapshot too long is not a good idea

##### Scenario 3
Make an interaction calling the following scenario (This is the basic idea that makes me create this plugin: to facilitate the actions of updates of the core jeedom while securing this update):
* Create a snapshot
* Update your Jeedom via Jeelink
* Schedule an ASK for snapshot removal in X days
* Delete or not the snapshot based on ASK response

##### Scenario 4
Send an alert if the Update available command on the ESXi informs us of the presence of an update so that we can plan to update it

##### Scenario 5
Monitor if a VM turns off, monitor if a VM no longer has its VMWARE Tools functional, etc ...

## Cron

The plugin is based on two crons
* cronHourly -> updates every hour information about your ESXi(s) and VMs
* cronDaily -> update once a day the presence or absence of update for your ESXi(s)

> This can be disabled in the vmware plugin configuration page
 <p align="center">
 <img src="https://github.com/TaGGoU91/jeedom_docs/blob/master/images/vmware/cron_plugin.png?raw=true" alt="List of Crons"/>
</p>


## FAQ

> If you have an status without icon for vmwares Tools, please let me know so I can add it


## Troubleshooting

> If you have any problem with the plugin, set the log in debug mode and communicate it to me via a [Private Message] (https://www.jeedom.com/forum/ucp.php?i=pm&mode=compose) on the Jeedom forum for me: TaG


## Changelog

[See the dedicated page](changelog.md).
