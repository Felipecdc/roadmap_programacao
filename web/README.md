# 🌐 Desenvolvimento Web

O desenvolvimento web engloba a criação de **sites**, **sistemas web**, **aplicações front-end** (interface com o usuário), **back-end** (lógica do servidor), e a **comunicação entre sistemas via APIs**.

---

## TCP (Transmission Control Protocol)

O **TCP** é um protocolo da camada de transporte da internet que garante a **comunicação confiável e ordenada entre dispositivos**.  
Ele estabelece uma conexão entre cliente e servidor antes de enviar dados, divide a informação em pacotes, confirma a entrega e reenvia caso haja perda.

### ⚙️ Como funciona o TCP?

<details>
- **Conexão orientada:** cliente e servidor “fazem um handshake” para iniciar a comunicação.
- **Divisão em pacotes:** os dados são fragmentados em pacotes menores para envio.
- **Confirmação:** o receptor envia confirmações para garantir que os pacotes chegaram.
- **Reenvio:** pacotes perdidos são reenviados automaticamente.
- **Ordenação:** os pacotes são reorganizados no destino para formar a mensagem original.
</details>

### 🖥️ Onde o TCP é usado?

<details>
TCP é usado para garantir que dados importantes cheguem completos e na ordem certa em aplicações como:

- Navegação web (HTTP/HTTPS)
- E-mails (SMTP, IMAP)
- Transferência de arquivos (FTP)
- Serviços de chat e muitos outros protocolos que precisam de confiabilidade
</details>

### ⚡ TCP x UDP

<details>

| Característica     | TCP                   | UDP                    |
| ------------------ | --------------------- | ---------------------- |
| Conexão            | Orientada, confiável  | Sem conexão, rápido    |
| Confirmação        | Sim                   | Não                    |
| Reenvio automático | Sim                   | Não                    |
| Uso comum          | Web, e-mail, arquivos | Streaming, jogos, VoIP |

</details>

---

## 🔁 HTTP Request

É uma **requisição feita pelo cliente (navegador, app, etc.) para o servidor**.  
Usa métodos como `GET`, `POST`, `PUT` e `DELETE` para enviar ou buscar dados de uma API.

<details>
  <summary>📌 Ver exemplo</summary>

```http
GET /produtos HTTP/1.1
Host: api.exemplo.com
```

</details>

---

## ⚙️ REST

REST é uma **arquitetura para APIs**.  
Utiliza métodos HTTP para executar operações de **CRUD** (Criar, Ler, Atualizar, Deletar) com base em URLs.

<details>
  <summary>📌 Ver exemplo</summary>

```
GET /usuarios
POST /usuarios
PUT /usuarios/1
DELETE /usuarios/1
```

</details>

<details>
  <summary>💬 Ver explicação</summary>
 
- É **stateless**, ou seja, cada requisição deve conter todas as informações necessárias (sem manter estado no servidor).
- Métodos **stateful** consistêm em guardar alguma informação em cache, banco, token e etc, como um chatbot que precisa lembrar do seu nome.

</details>

---

## 🔗 Web Services

Serviços que permitem a **comunicação entre sistemas na rede**. Os principais tipos são:

- **REST**: usa HTTP, mais leve, trabalha com JSON
- **SOAP**: baseado em XML, mais robusto e padronizado

<details>
  <summary>💬 Ver explicação</summary>

Usados, por exemplo, quando um sistema de loja precisa se comunicar com uma API de pagamento, envio ou estoque.

</details>

---

## 🧾 Headers HTTP

Os **headers** carregam informações adicionais na requisição ou resposta HTTP, como tipo de conteúdo, autorização e idioma.

<details>
  <summary>📌 Ver exemplo</summary>

```http
Content-Type: application/json
Authorization: Bearer abc123
Accept-Language: pt-BR
```

</details>

---

## 📊 Status Codes HTTP

Os **status codes** indicam o resultado de uma requisição HTTP.

<details>
  <summary>📌 Ver principais códigos</summary>

- `200 OK`: sucesso
- `201 Created`: recurso criado
- `400 Bad Request`: erro do cliente
- `401 Unauthorized`: não autenticado
- `404 Not Found`: recurso não encontrado
- `500 Internal Server Error`: erro no servidor

</details>

<details>
  <summary>💬 Ver explicação</summary>

Eles são agrupados em categorias:

- `1xx`: informativos
- `2xx`: sucesso
- `3xx`: redirecionamentos
- `4xx`: erros do cliente
- `5xx`: erros do servidor

</details>

---

📌 _Resumo escrito por Felipe Castro — voltado para estudos e concursos na área de Desenvolvimento Web._
