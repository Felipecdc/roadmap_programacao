# 🗄️ Conceitos de Banco de Dados

Banco de Dados é um sistema que permite armazenar, organizar e acessar dados de forma estruturada, segura e eficiente.  
É essencial para qualquer aplicação que precise lidar com informações persistentes, como usuários, produtos, pedidos etc.

---

## 🔗 Modelo Entidade-Relacionamento (MER)

Representa entidades (como Cliente, Produto) e os **relacionamentos** entre elas (como Pedido, Compra).

<details>
  <summary>💬 Explicação</summary>

Uma **entidade** representa algo do mundo real, com atributos próprios.  
Os **relacionamentos** mostram como essas entidades se conectam.

### Cardinalidade

Indica a quantidade de relacionamentos possíveis entre as entidades:

| Símbolo | Significado        |
| ------- | ------------------ |
| 1:1     | Um para um         |
| 1:N     | Um para muitos     |
| N:1     | Muitos para um     |
| N:N     | Muitos para muitos |

```diff
[Cliente]     1:N      [Pedido]        N:1       [Pagamento]
+ id         ---->     + id           ---->      + id
+ nome                 + data                    + valor
+ email                + cliente_id              + pedido_id

```

</details>

---

## 🧾 Diagrama Entidade-Relacionamento (DER)

É a **representação visual** do MER usando símbolos gráficos.

<details>
  <summary>📌 Ver exemplo simbólico</summary>

- 🟦 Retângulo → Entidade
- 🔵 Elipse → Atributo
- 🔷 Losango → Relacionamento
- ➖ Linha → Conexão entre eles

</details>

---

## 🧹 Normalização \*\*\*\* estudar mais esse

Processo que visa **reduzir redundância e dependência de dados**, organizando as tabelas em formas normais.

<details>
  <summary>💬 Explicação</summary>

Existem várias formas normais (1FN, 2FN, 3FN...).  
A ideia é **evitar repetição de dados**, separar em tabelas distintas e manter consistência.

</details>

---

## 🔐 Segurança

Refere-se à **proteção dos dados** contra acessos não autorizados.

<details>
  <summary>🔒 Práticas comuns</summary>

- Controle de acesso com permissões
- Criptografia de dados sensíveis
- Hash de senhas e códigos sensíveis
- Backup e auditoria

</details>

---

## 🔄 Integridade Referencial - FK

Garante que as **chaves estrangeiras (foreign keys)** referenciem registros válidos.

<details>
  <summary>📌 Exemplo</summary>

Se um pedido tem uma coluna `cliente_id`, o valor dela deve existir na tabela `clientes`.

</details>

---

## 💾 Backup

Cópia de segurança do banco de dados que pode ser usada para **recuperação em caso de falhas**.

<details>
  <summary>💬 Explicação</summary>

Pode ser feito manualmente ou de forma automatizada, e armazenado em locais diferentes (nuvem, servidor local).

</details>

---

## 🔍 Índice

Usado para **aumentar a performance das buscas** no banco de dados.

<details>
  <summary>📌 Exemplo</summary>

Criar um índice em uma coluna como `email` pode acelerar a consulta:

```sql
CREATE INDEX idx_email ON usuarios(email);
```

</details>

---

## ⚙️ ACID

Conjunto de propriedades que garantem a **confiabilidade** nas transações:

- **Atomicidade**: tudo ou nada
- **Consistência**: garante integridade dos dados
- **Isolamento**: transações independentes
- **Durabilidade**: dados persistem mesmo após falhas

---

## 🔁 Transações

Conjunto de operações que são executadas como uma **unidade atômica**.

<details>
  <summary>📌 Exemplo SQL</summary>

```sql
BEGIN;

UPDATE contas SET saldo = saldo - 100 WHERE id = 1;
UPDATE contas SET saldo = saldo + 100 WHERE id = 2;

COMMIT;
```

</details>

---

## 🗝️ Extra: Chave Primária

Identifica **unicamente** um registro em uma tabela.

<details>
  <summary>📌 Exemplo</summary>

```sql
CREATE TABLE clientes (
  id SERIAL PRIMARY KEY,
  nome TEXT
);
```

</details>

---

## 🛠️ Extra: SQL

**Structured Query Language**, linguagem padrão para manipulação de dados em **bancos de dados relacionais**.

| Sigla   | Nome Completo                | O que faz                                                    |
| ------- | ---------------------------- | ------------------------------------------------------------ |
| **DML** | Data Manipulation Language   | Manipula dados dentro das tabelas (ex: `SELECT`, `INSERT`)   |
| **DDL** | Data Definition Language     | Define e modifica estrutura do banco (ex: `CREATE`, `ALTER`) |
| **DCL** | Data Control Language        | Controla permissões e acessos (ex: `GRANT`, `REVOKE`)        |
| **TCL** | Transaction Control Language | Controla transações no banco (ex: `COMMIT`, `ROLLBACK`)      |

<details>
<summary>Mais comandos</summary>

### 📌 Comandos Básicos (DML - Manipulação de Dados)

| Comando | Função                    |
| ------- | ------------------------- |
| SELECT  | Consulta/busca dados      |
| INSERT  | Insere novos registros    |
| UPDATE  | Atualiza dados existentes |
| DELETE  | Remove registros          |

---

### 🏗️ Comandos de Definição de Dados (DDL)

| Comando  | Função                                               |
| -------- | ---------------------------------------------------- |
| CREATE   | Cria banco, tabelas, views, etc.                     |
| ALTER    | Altera estrutura de uma tabela                       |
| DROP     | Exclui banco, tabela ou view                         |
| TRUNCATE | Remove todos os dados da tabela (sem log de remoção) |

---

### 🔐 Comandos de Controle de Permissão (DCL)

| Comando | Função                        |
| ------- | ----------------------------- |
| GRANT   | Concede permissões a usuários |
| REVOKE  | Remove permissões de usuários |

---

### 🔄 Comandos de Controle de Transação (TCL)

| Comando   | Função                                |
| --------- | ------------------------------------- |
| BEGIN     | Inicia uma transação                  |
| COMMIT    | Confirma as alterações da transação   |
| ROLLBACK  | Desfaz alterações em caso de erro     |
| SAVEPOINT | Define um ponto para possível retorno |

---

### 🔍 Comandos de Consulta Avançada

| Comando            | Função                                                              |
| ------------------ | ------------------------------------------------------------------- |
| WHERE              | Filtra os resultados da consulta                                    |
| ORDER BY           | Ordena os resultados (ASC ou DESC)                                  |
| GROUP BY           | Agrupa registros para funções agregadas (ex: `SUM`, `COUNT`, `AVG`) |
| HAVING             | Filtra grupos criados pelo `GROUP BY`                               |
| DISTINCT           | Remove duplicatas dos resultados                                    |
| LIMIT / OFFSET     | Controla a quantidade de registros retornados                       |
| BETWEEN            | Filtra valores dentro de um intervalo (ex: `BETWEEN 10 AND 100`)    |
| LIKE               | Busca por padrões de texto (ex: `LIKE '%nome%'`)                    |
| IN                 | Verifica se o valor está em uma lista (ex: `IN ('SP', 'RJ', 'MG')`) |
| IS NULL / NOT NULL | Verifica se valores são nulos ou não                                |

---

### 🔗 Comandos de Junção (JOINs)

| Tipo de JOIN | Função                                                                      |
| ------------ | --------------------------------------------------------------------------- |
| INNER JOIN   | Retorna apenas os registros que têm correspondência nas duas tabelas        |
| LEFT JOIN    | Retorna todos os registros da tabela da esquerda, mesmo sem correspondência |
| RIGHT JOIN   | Retorna todos os registros da tabela da direita, mesmo sem correspondência  |
| FULL JOIN    | Retorna registros com ou sem correspondência nas duas tabelas               |
| SELF JOIN    | Junta a tabela com ela mesma                                                |

---

### 📦 Outros Recursos Úteis

| Comando    | Função                                                                           |
| ---------- | -------------------------------------------------------------------------------- |
| AS         | Define um alias (apelido) para colunas ou tabelas (ex: `SELECT nome AS cliente`) |
| WITH       | Define subconsultas temporárias nomeadas (CTE - Common Table Expression)         |
| CASE       | Estrutura condicional em uma consulta (como um `if`)                             |
| UNION      | Une os resultados de duas ou mais consultas (sem duplicatas)                     |
| UNION ALL  | Une os resultados de duas ou mais consultas (com duplicatas)                     |
| EXISTS     | Verifica se uma subconsulta retorna algum resultado                              |
| NOT EXISTS | Retorna se a subconsulta **não** retorna nenhum resultado                        |

---

🧠 **Dica**: Sempre combine esses comandos com boas práticas de índice e normalização para manter o desempenho e integridade do banco de dados.

</details>

</details>

---

📌 _Resumo escrito por Felipe Castro — ideal para estudos e concursos sobre Banco de Dados._
