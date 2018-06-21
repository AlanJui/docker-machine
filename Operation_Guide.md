

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
```

```
docker-ls
```

```
docker-machine ssh myvm1 docker swarm init --advertise-addr 192.168.99.100
```

```
docker swarm join-token manager
```

```
docker-machine ssh myvm2 docker swarm join --token <TOKEN>
```



## Start up App in Swarm

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
