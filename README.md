# Projeto rotten-potatoes

## Sobre o projeto
O projeto Rotten-Potatoes é um projeto desenvolvido em Python e um banco MongoDB.
Neste repositório, estamos utilizando também para o Desafio **Kubernetes Fundamentos.**

## Configuração
MONGODB_DB => Nome do database<br>
MONGODB_HOST => Host do MongoDB<br>
MONGODB_PORT => Posta de acesso ao MongoDB<br>
MONGODB_USERNAME => Usuário do MongoDB<br>
MONGODB_PASSWORD => Senha do MongoDB<br>

### Observações do projeto
A aplicação é exposta: <br>
**docker compose** Usando a porta 8080<br>
**Kubernetes** Usando o ingress bare metal na porta 80<br>

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

**Docker Hub - [giozandonai/rotten-potatoes](https://hub.docker.com/u/giozandonai/rotten-potatoes)

**Rodando compose:**
`$ docker-compose --env-file .env up -d`

## Subindo com DOCKER COMPOSE
**Acessando a aplicação:**
`http://localhost:8080`

**Acessando mongo-express:**
`http://localhost:8090`

## Subindo com KUBERNETES (sem mongo-express)
Acessar a pasta ./k8s:<br>
`kubectl apply -f . -R`<br>
`http://nome_dominio`<br>