## Docker installation:

```
yum install docker -y
```
### adding user into docker group or 
### Change the permissions of `/var/run/docker.sock` for the current user.

```
usermod -a -G docker $USER

sudo chown $USER /var/run/docker.sock
```
### Restart docker
```
systemctl enable docker
systemctl start docker
systemctl status docker
```

## To download and install Compose standalone, run:
```
curl -SL https://github.com/docker/compose/releases/download/v2.26.0/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose
```
```
sudo ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose
```
```
chmod 777 /usr/bin/docker-compose
```
* Defining a Custom Bridge Network:

```
networks:
  my_custom_bridge_network:
    driver: bridge
```
This configuration defines a custom bridge network named my_custom_bridge_network. This network will be created internally by Docker Compose and will only be accessible to services defined within the same docker-compose.yml file.

* Using an External Network:
```
networks:
  default:
    external:
      name: my_custom_bridge_network
```
This configuration specifies that the service(s) defined in the Docker Compose file should use an external network named my_custom_bridge_network. This network is expected to be created outside of Docker Compose, and the services will connect to it. The external keyword indicates that the network is not managed by Docker Compose and already exists in the Docker environment.

### In summary:

The first configuration creates an internal custom bridge network specifically for use within the Docker Compose project.
The second configuration references an external network that already exists in the Docker environment and allows services in the Docker Compose project to connect to it.