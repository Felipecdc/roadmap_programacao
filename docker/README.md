# 🐳 Docker – Plataforma de Contêineres

**Docker** é uma plataforma que facilita a criação, distribuição e execução de aplicações dentro de **contêineres**. Um contêiner é uma unidade leve, portátil e isolada que contém tudo que a aplicação precisa para rodar, garantindo que ela funcione igual em qualquer ambiente.

---

## 🧭 Por que usar Docker?

- Isolamento e consistência de ambientes
- Facilita o desenvolvimento e deploy contínuo (CI/CD)
- Portabilidade entre máquinas e servidores
- Rápida inicialização em comparação a máquinas virtuais
- Compartilhamento e versionamento de imagens (Docker Hub)
- Escalabilidade em produção com orquestradores (Kubernetes, Docker Swarm)

---

## ⚙️ Conceitos Básicos

| Conceito       | Descrição                                                                 |
| -------------- | ------------------------------------------------------------------------- |
| Imagem         | Template imutável para criar contêineres, contendo aplicação e libs       |
| Contêiner      | Instância em execução de uma imagem, isolada do sistema host              |
| Dockerfile     | Arquivo texto com instruções para criar uma imagem Docker                 |
| Docker Hub     | Repositório público/privado para armazenar imagens Docker                 |
| Volume         | Área persistente para dados entre contêineres e host                      |
| Network        | Rede virtual que conecta contêineres entre si ou ao host                  |
| Docker Compose | Ferramenta para definir e rodar múltiplos contêineres com um arquivo YAML |

---

## 🧾 Principais Comandos Docker

<details>
<summary>🐳 Imagens</summary>

```bash
# Criar imagem a partir do Dockerfile na pasta atual, com tag
docker build -t minha-imagem:1.0 .

# Listar imagens locais

docker images

# Remover imagem pelo nome ou ID

docker rmi minha-imagem:1.0

```

</details>

---

<details>
<summary>🐳 Contêineres</summary>

```bash
# Rodar um contêiner interativo a partir de uma imagem (ex: ubuntu)
docker run -it ubuntu /bin/bash

# Rodar um contêiner em background (detached) mapeando portas
docker run -d -p 8080:80 minha-imagem:1.0

# Listar contêineres em execução
docker ps

# Listar todos os contêineres (ativos e parados)
docker ps -a

# Parar um contêiner pelo ID ou nome
docker stop <container_id>

# Remover um contêiner parado
docker rm <container_id>

# Ver logs de um contêiner
docker logs <container_id>

# Acessar um contêiner em execução com shell
docker exec -it <container_id> /bin/bash

```

</details>

---

<details>
<summary>🐳 Dockerfile</summary>

```bash
# Exemplo básico de Dockerfile para uma aplicação Node.js

# Usar imagem base oficial do Node.js (versão 18)
FROM node:18-alpine

# Definir diretório de trabalho dentro do container
WORKDIR /app

# Copiar package.json e package-lock.json para instalar dependências
COPY package*.json ./

# Instalar dependências
RUN npm install

# Copiar todo o código da aplicação para o container
COPY . .

# Expôr a porta que a aplicação vai usar
EXPOSE 3000

# Comando para rodar a aplicação
CMD ["npm", "start"]


```

### O que é o Dockerfile?

É um arquivo de texto com instruções para construir uma imagem Docker, definindo a base, cópias de arquivos, instalação de dependências, comandos para rodar e mais.

### Principais comandos Dockerfile

```bash
FROM alpine              # Define a imagem base
WORKDIR /app             # Define o diretório de trabalho
COPY . .                 # Copia arquivos do host para o container
RUN apk add curl         # Executa comandos no build (instalar pacotes)
EXPOSE 80                # Expõe porta para fora do container
CMD ["command", "arg"]   # Comando padrão ao iniciar o container
ENTRYPOINT ["entrypoint"]# Comando fixo que sempre roda no container

```

</details>

---

<details>
<summary>🐳 Docker Hub</summary>

```bash
# Logar na sua conta Docker Hub
docker login

# Marcar (tag) uma imagem local para enviar ao Docker Hub
docker tag minha-imagem:1.0 seuusuario/minha-imagem:1.0

# Enviar (push) a imagem para o Docker Hub
docker push seuusuario/minha-imagem:1.0

# Baixar (pull) uma imagem pública do Docker Hub
docker pull nginx:latest

# Listar imagens locais
docker images

```

### O que é o Docker Hub?

É um repositório online onde você pode armazenar e compartilhar imagens Docker, públicas ou privadas, para usar em qualquer lugar.

</details>

---

<details>
<summary>🐳 Volumes e Persistência</summary>

```bash
# Criar um volume nomeado
docker volume create meu-volume

# Rodar contêiner montando volume para persistência
docker run -d -v meu-volume:/app/data minha-imagem

# Listar volumes
docker volume ls

# Remover volume (certifique-se que não está em uso)
docker volume rm meu-volume

```

</details>

---

<details>
<summary>🐳 Redes</summary>

```bash
# Listar redes Docker
docker network ls

# Criar rede customizada
docker network create minha-rede

# Rodar contêiner conectado a rede customizada
docker run -d --network minha-rede minha-imagem

```

</details>

---

<details>
<summary>🐳 Docker Compose</summary>

```bash
version: "3.8"

services:
  web:
    build: .
    ports:
      - "8080:80"
    volumes:
      - .:/app
    networks:
      - app-net

  db:
    image: postgres:13
    environment:
      POSTGRES_USER: user
      POSTGRES_PASSWORD: senha
      POSTGRES_DB: meu_banco
    volumes:
      - pgdata:/var/lib/postgresql/data
    networks:
      - app-net

volumes:
  pgdata:

networks:
  app-net:

```

```bash
# Comandos Docker Compose
docker compose up         # Sobe os serviços definidos (modo interativo)
docker compose up -d      # Sobe em modo detached (background)
docker compose down       # Para e remove containers, redes, volumes criados
docker compose logs       # Ver logs dos serviços
docker compose ps         # Listar serviços em execução
```

</details>

---

## 📝 Quando usar Docker?

- Para garantir que seu ambiente de desenvolvimento seja igual ao de produção.
- Para facilitar o deploy em servidores ou nuvens diferentes.
- Para isolar serviços, tornando mais fácil cuidar e ampliar cada parte do sistema.
- Para rodar bancos de dados e outras ferramentas locais sem precisar instalar no computador.
- Para testar versões diferentes de programas sem problemas.

---

## 📚 Dicas para usar Docker

- Use o arquivo `.dockerignore` para não copiar arquivos que não precisa na imagem.
- Prefira imagens leves, como a `alpine`, para deixar tudo mais rápido e pequeno.
- Sempre fixe as versões das imagens para evitar erros com atualizações automáticas.
- Use builds com várias etapas (multistage) para deixar a imagem final menor e mais limpa.
- Escreva comentários nos arquivos para facilitar o entendimento.

---

## 🔗 Links úteis

- [Documentação oficial Docker](https://docs.docker.com/)
- [Docker Hub](https://hub.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

📌 _Resumo escrito por Felipe Castro — ideal para estudos de Git, entrevistas técnicas e concursos._
