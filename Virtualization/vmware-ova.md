# Export VM to OVA

You will need the vmware OVF tool to
[download this click this (you will need a vmware customer connect account to do so)
](https://customerconnect.vmware.com/downloads/details?downloadGroup=OVFTOOL400&productId=353&download=true&fileId=9ccfd5129341c2b4634c994cd32888c7&uuId=2311bf05-4997-4945-a5fc-e66de44bbf56)



1. Install current version of VMware ESXI OVF tool (ofv and ova)
2. Shut down the VM you need to export
4. Run this: >.\ovftool.exe --allowExtraConfig vi://10.5.5.122/VDI-08r2 "c:\vmexp\vdi-08r2.ova"