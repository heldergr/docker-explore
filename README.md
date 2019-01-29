# Docker commands

## build

Cria uma imagem com base em um Dockerfile.

*Parâmetros*:   
* -t: nome da imagem a ser criada   
* -f: arquivo Dockerfile ("Dockerfile" é o default)   

*Exemplo*:  
docker build -t nginx-videojs .

## run

Executa um comando em um novo container.

*Parâmetros*:   
* -d: executa parâmetro em background e exibe o id do container
* --name: atribui um nome ao container
* -p: mapeamento de porta do container para porta local
* -v: mapeamento de volume local para pasta dentro do container
* -w: diretório corrente dentor do container

*Exemplo*:  
docker run --name cn-nginx-videojs -d -p 8080:80 nginx-videojs

## start

Executa um ou mais containers parados.

*Exemplo*:  
docker start *CONTAINER_ID*

## stop

Para um container em execução.

*Exemplo*:  
docker stop *CONTAINER_ID*

