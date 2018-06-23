# 專案操作指引

Build Docker Image
==================

```
docker build -t demo .
```

```
docker login
```

```
docker tag demo alanjui/docker-swarm:0.0.1
```

```
docker push alanjui/docker-swarm:0.0.1
```

```
docker pull alanajui/docker-swarm:0.0.1
```

---


Start Docker-Machine
====================

```
docker-machine create --driver virtualbox myvm1
docker-machine create --driver virtualbox myvm2
```

```
docker-machine ls
```

```
docker-machine ssh myvm1 docker swarm init --advertise-addr 192.168.99.100
```

```
docker swarm join-token manager
```

```
docker-machine ssh myvm2 docker swarm join --token <TOKEN> 192.168.99.100:2377
```

```
docker-machine ssh myvm1 docker node ls
```



## Start up App in Swarm

```
docker-machine env myvm1
eval $(docker-machine env myvm1)
```

```
docker stack deploy -c docker-stack.yml myapp-01
```



## Take down App and the Swarm

Executing the commands listed below on myvm1 (Swarm Manager Machine)

Take App down from stack:
```
docker stack rm myapp-01
```

Take down the Swarm:
```
docker swarm leave --force
```


```
eval $(docker-machine env -u)
```