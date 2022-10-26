# This would be similar accross both when deploying


installing k3s node

# Prep for all Host and nodes
```bash
sudo iptables -F 
sudo update-alternatives --set iptables /usr/sbin/iptables-legacy 
sudo update-alternatives --set ip6tables /usr/sbin/ip6tables-legacy 

sudo reboot
```

## Node Install
```bash
curl -sfL https://get.k3s.io | K3S_TOKEN="Your Token" K3S_URL="https://k3s host:6443" K3S_NODE_NAME="node name" sh -
```


# Host install
### Needs to be done as root

```bash
sudo bash
```
```bash
curl -sfL https://get.k3s.io | K3S_KUBECONFIG_MODE="644" sh -s -
# Get your key
sudo cat /var/lib/rancher/k3s/server/node-token
```

# Installing into Portainer
```bash
kubectl apply -f https://downloads.portainer.io/ce2-15/portainer-agent-k8s-lb.yaml
```
