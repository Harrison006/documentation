# Licensing

you can use the free license, however it limits you to 8 cores per vm, and you cant install vcenter

Best way to get around that is go on evaluation mode and

```bash
rm -r /etc/vmware/license.cfg
```
This resets the evaluation time, this is infinite but a pain in the ass

just use xen lol