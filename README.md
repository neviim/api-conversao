# API de conversão F/C & C/F

## fahrenheit/celsius
```zsh
curl http://192.168.0.44:8080/fahrenheit/0/celsius
{
"celsius": -17,77
}

```

## celsius/fahrenheit
```zsh
http://192.168.0.44:8080/celsius/0/fahrenheit
{
"fahrenheit": 32
}
```

## docker build
```zsh
# dentro do diretorio rais da aplicação.
$ docker build -t neviim/api-conversao:v1 .

# checando se a images foi criada, maquina local.
$ docker image ls
REPOSITORY              TAG   IMAGE ID        CREATED          SIZE
neviim/api-conversao    v1    0e672d309988    4 minutes ago    121MB

$ docker container run -p 8080:8080 -d neviim/api-conversao:v1
5109f18c595474925ecca2d0c7b9f6414a56f723c15332b9abba0ef47b1b6f0a

$ docker container ls 
CONTAINER ID        IMAGE                     COMMAND                  CREATED             STATUS              PORTS                    NAMES
5109f18c5954        neviim/api-conversao:v1   "docker-entrypoint.s…"   38 seconds ago      Up 36 seconds       0.0.0.0:8080->8080/tcp   infallible_pasteur

# altentica no hub docker.
$ docker login
Login Succeeded

# publica o container nesta conta.
$ docker push neviim/api-conversao:v1

$ docker tag neviim/api-conversao:v1 neviim/api-conversao:latest
# como todas as camadas existem ele só adiciona a tag
$ docker push neviim/api-conversao:latest 

# testando se o container esta funcionando
$ docker container rm -f 5109f18c5954
$ docker image ls

$ docker image rm -f 0e672d309988 #neviim/api-conversao:latest
$ docker image rm -f 6a2955643b9e #neviim/api-conversao:v1

# sera baixando novamente agora do repositorio hub.docker.com
$ docker container run -d -p 8080:8080 neviim/api-conversao:v1

$ docker container ls
CONTAINER ID        IMAGE                     COMMAND                  ...
b3b15b392446        neviim/api-conversao:v1   "docker-entrypoint.s…"   ...
```

## Colocando este container para rodar na nuvem - Azure App Server
```zsh
# crie uma conta Azure Account free
https://azure.com/
```
