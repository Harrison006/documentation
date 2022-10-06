# Basic ASS config of nftables
this is the most bassic config with ssh 22 port forward (**obviously dont use in real case**)

```yaml
table ip thetable {
        chain kfc {
                type filter hook input priority filter; policy accept;
                ct state established,related accept
                iifname "enp0s31f6.2" drop
        }

        chain maccas {
                type nat hook postrouting priority filter; policy accept;
                oifname "enp0s31f6.2" masquerade
        }
}
```
## Ip forwarding
Make sure you enable ip forwarding under 
sysctl -w net.ipv4.ip_forward=1

OR
```bash
sudo nano /etc/sysctl.conf
```
And find the line that is # out
And make sure it looks like 
```
net.ipv4.ip_forward = 1
```
NOT
```
#net.ipv4.ip_forward = 1
```