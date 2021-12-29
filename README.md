# CONVERSÃO TEMPERATURA

Essa aplicação foi escrita em Node Js e usada para exercitar os conhecimentos de Docker no curso Kubedev.

## Etapas para criação da imagem:
1- Utilizar uma versão do node e não a versão latest da imagem. Para que possamos garantir a idepotência da nossa imagem.

```docker
FROM node:14.17.5
````
2-Definir o diretório de trabalho da aplicação dentro da imagem a ser criada.

```docker
WORKDIR /app
````
3- Copiar todos os arquivos *package.json para dentro do diretório de trabalho da imagem

```docker
COPY package*.json ./
```
4- Executar o comando para baixar as dependências necessárias para rodar a nossa aplicação.

```docker
RUN npm install
```
5- Copiar os arquivos da aplicação do diretório local para o diretório de trabalho da imagem.

```docker
COPY . .
```
6- Expor a porta 8080 para acessar a aplicação.

```docker
EXPOSE 8080

```
7- Executar o comando para iniciar a aplicação.

```docker
CMD ["node","server.js"]
```
Como boa prática, nós devemos sempre criar um arquivo **.gitignore** para não copiarmos para dentro da nossa imagem arquivos desnecessários para o funcionamento da nossa aplicação. Para esta imagem o nosso arquivo ficou com o seguinte conteúdo:

```docker
.git
.gitignore
README.md
node_modules
Dockerfile
```


