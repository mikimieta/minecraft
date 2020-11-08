# minecraft

## install docker

https://www.docker.com/get-started

## deploy minecraft stack

```sh
docker --host ssh://ubuntu@54.38.137.98 stack deploy --compose-file docker-compose.yml --prune minecraft
docker --host ssh://ubuntu@54.38.137.98 service logs minecraft_minecraft -f
```

# configure minecraft

```sh
docker --host ssh://ubuntu@51.83.254.60 cp 23319bd8188f:/data/server.properties data/
docker --host ssh://ubuntu@51.83.254.60 cp 23319bd8188f:/data/plugins data/
scp -r plugins ubuntu@51.83.254.60:plugins
```


# run rcon-cli in minecraft container

```sh
docker --host ssh://ubuntu@51.83.254.60 exec -it $(docker --host ssh://ubuntu@51.83.254.60 ps -q -f name=minecraft) rcon-cli
```

## monitor minecraft stack

```sh
telnet 54.38.137.98 25565
docker service ls
docker service logs minecraft_minecraft -f
```

## remove minecraft stack
```sh
docker --host ssh://ubuntu@54.38.137.98 stack rm minecraft
```
