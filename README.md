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
docker swarm init --advertise-addr 172.17.0.11
