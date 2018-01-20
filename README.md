# docker-swarm
Docker Swarm Using Vagrant

## Prereqs
```
vagrant plugin install vagrant-hostmanager
```

## Cluster Setup
Run the below commands to setup a 3 node CentOS cluster with docker-ce installed 

```
git clone https://github.com/nitnagpal/docker-swarm.git
cd docker-swarm
vagrant up
```

## SSHing into machines

```
vagrant ssh docker-01
vagrant ssh docker-02
vagrant ssh docker-03
```

## Initializing Swarm Cluster
```
docker swarm init --advertise-addr 172.17.0.11
```

## To add a worker
```
docker swarm join --token <TOKEN> 172.17.0.11:2377
```

## Get join token for worker
```
docker swarm join-token worker
```

## Get join token for manager
```
docker swarm join-token manager
```

## Locking swarm cluster on initializing
```
docker swarm init --autolock --advertise-addr 172.17.0.11
```

## Locking a running swarm cluster
```
docker swarm update --autolock=true
```

## Get swarm cluster unlock key
```
docker swarm unlock-key
```

## Rotate swarm cluster unlock Key
```
docker swarm unlock-key --rotate
```
