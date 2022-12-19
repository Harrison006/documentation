# Export VM to OVA


1. Install current version of VMware vSphere Power CLI
2. Shut down the VM you need to export
3. Connect the Power CLI app to your vCenter (when the power CLI launches it tells you the command to run to connect it to a vCenter FQDN)
4. Run this: >Export-VApp -Destination "C:\Directory" -VM "Name-of-vm-In-vCenter" -Format Ova