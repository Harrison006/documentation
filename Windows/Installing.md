# Installing Windows Server 20XX


## Installing with boot iso
installing with a boot iso is as simple as using a tool like rufus and loading your server 20XX iso onto it

When installing make sure to have only 1 disk plugged in as windows installer has a bug that installs boot loader into 2nd disk

Installing windows server onto a drive with 50GB or greater is ideal and if the server is for MECM check here MECM SETUP
#
## Activation

Downloading a Evaluation copy means you would need to run the following commands to activate it

```
DISM.exe /online /Set-Edition:ServerStandard /ProductKey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /AcceptEula

DISM.exe /online /Set-Edition:Datacenter /ProductKey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /AcceptEula
```
Other commands you may need to run are:
To activate your Windows Server:
1. Enter key via GUI or run the command: 
``` 
slmgr.vbs /ipk XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```
To get the available editions:
1. Open an elevated command prompt.
2. Run the following command: DISM.exe /Online /Get-TargetEditions

