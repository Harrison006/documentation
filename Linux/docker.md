# Ubuntu Docker
Installing docker can be easily done from here https://docs.docker.com/engine/install/ubuntu/

# Portainer Swarm
```bash
Installing portainer can be easily done by 
docker network create \
--driver overlay \
  portainer_agent_network

docker service create \
  --name portainer_agent \
  --network portainer_agent_network \
  -p 9001:9001/tcp \
  --mode global \
  --constraint 'node.platform.os == linux' \
  --mount type=bind,src=//var/run/docker.sock,dst=/var/run/docker.sock \
  --mount type=bind,src=//var/lib/docker/volumes,dst=/var/lib/docker/volumes \
  portainer/agent:2.15.0
  ```
# Portainer Single
```bash
docker run -d \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v /var/lib/docker/volumes:/var/lib/docker/volumes \
  -v /:/host \
  -v portainer_agent_data:/data \
  --restart always \
  -e EDGE=1 \
  -e EDGE_ID=69c8e738-c2fa-46ff-8914-eaa4eddc3cce \
  -e EDGE_KEY=yourkey \
  -e EDGE_INSECURE_POLL=1 \
  --name portainer_edge_agent \
  portainer/agent:2.15.0
  ```
  