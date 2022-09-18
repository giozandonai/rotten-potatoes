# Projeto rotten-potatoes

## Sobre o projeto
O projeto Rotten-Potatoes é um projeto desenvolvido em Python e um banco MongoDB.

## Configuração

MONGODB_DB => Nome do database
MONGODB_HOST => Host do MongoDB
MONGODB_PORT => Posta de acesso ao MongoDB
MONGODB_USERNAME => Usuário do MongoDB
MONGODB_PASSWORD => Senha do MongoDB

### Observações do projeto
A aplicação é exposta usando a porta 8080

**srv/Dockerfile**
```
FROM python:3.8-slim-buster
WORKDIR /app
COPY requirements.txt .
RUN python -m pip install --upgrade pip && pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD gunicorn --bind 0.0.0.0:5000 -c config.py app:app
```

**Docker Hub - [giozandonai/rotten-potatoes](https://hub.docker.com/u/giozandonai/rotten-potatoes)**

**Rodando compose:**
`$ docker-compose --env-file .env up -d`

**Acessando a aplicação:**
`http://localhost:8080`

**Acessando mongo-express:**
`http://localhost:8090`

