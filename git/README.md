# 🌳 Git – Sistema de Controle de Versão

**Git** é um sistema de controle de versão distribuído que permite acompanhar, registrar e gerenciar o histórico de alterações em arquivos e projetos, especialmente de código-fonte.

---

## 🧭 Por que usar o Git?

- Controle de histórico de alterações
- Trabalho em equipe com merge e branches
- Restauração de versões anteriores
- Integração com plataformas como **GitHub**, **GitLab**, **Bitbucket**

---

## ⚙️ Conceitos Básicos

| Conceito     | Descrição                                                            |
| ------------ | -------------------------------------------------------------------- |
| Repositório  | Pasta contendo todos os arquivos versionados e o histórico (`.git/`) |
| Commit       | Registro de alteração (snapshot)                                     |
| Branch       | Linha de desenvolvimento independente                                |
| Merge        | Combina mudanças de branches diferentes                              |
| Staging Area | Área intermediária entre modificações e o commit final               |
| HEAD         | Ponteiro que aponta para o commit atual                              |

---

## 🧾 Principais Comandos Git

<details>
<summary><strong>📥 git clone</strong></summary>

Clona (baixa) um repositório remoto para sua máquina local.

```bash
git clone https://github.com/usuario/repositorio.git
```

📝 **Usar quando:** você está começando a trabalhar em um projeto já existente.

📌 **Depois de:** criar ou obter acesso ao repositório remoto.  
📌 **Antes de:** fazer alterações, criar branches, etc.

</details>

---

<details>
<summary><strong>📦 git init</strong></summary>

Inicializa um novo repositório Git em uma pasta local.

```bash
mkdir meu-projeto && cd meu-projeto
git init
```

📝 **Usar quando:** você está criando um projeto novo do zero e quer começar a versionar com Git.

📌 **Depois de:** criar a pasta do projeto.  
📌 **Antes de:** adicionar arquivos e fazer o primeiro commit.

</details>

---

<details>
<summary><strong>📝 git add</strong></summary>

Adiciona arquivos ao **staging area** (pré-commit).

```bash
git add arquivo.txt
git add .        # adiciona todos os arquivos modificados
```

📝 **Usar quando:** você fez alterações e quer incluí-las no próximo commit.

📌 **Depois de:** modificar ou criar arquivos.  
📌 **Antes de:** usar `git commit`.

</details>

---

<details>
<summary><strong>📌 git commit</strong></summary>

Grava as alterações no histórico do repositório.

```bash
git commit -m "mensagem descritiva do commit"
```

📝 **Usar quando:** você terminou uma tarefa, corrigiu algo ou deseja salvar um estado específico do código.

📌 **Depois de:** `git add`  
📌 **Antes de:** `git push` (se for enviar ao remoto)

</details>

---

<details>
<summary><strong>📤 git push</strong></summary>

Envia os commits locais para o repositório remoto.

```bash
git push origin main
```

📝 **Usar quando:** você quer compartilhar suas alterações com os outros no repositório remoto.

📌 **Depois de:** `git commit`  
📌 **Antes de:** outras pessoas fazerem `git pull`

</details>

---

<details>
<summary><strong>📥 git pull</strong></summary>

Atualiza seu repositório local com o remoto (fetch + merge).

```bash
git pull origin main
```

📝 **Usar quando:** antes de começar um novo trabalho, para ter a versão mais recente.

📌 **Depois de:** um tempo sem atualizar o projeto  
📌 **Antes de:** começar uma nova alteração

</details>

---

<details>
<summary><strong>🔀 git branch</strong></summary>

Cria ou lista branches (ramificações de desenvolvimento).

```bash
git branch              # lista as branches
git branch nova-feature
```

📝 **Usar quando:** quer trabalhar em algo novo sem afetar o código principal.

📌 **Depois de:** decidir separar um novo fluxo de trabalho  
📌 **Antes de:** `git checkout nova-feature`

</details>

---

<details>
<summary><strong>🔁 git checkout</strong></summary>

Muda para outro branch ou commit.

```bash
git checkout main
git checkout -b nova-feature  # cria e já muda para o novo branch
```

📝 **Usar quando:** precisa alternar entre versões ou iniciar um novo branch.

📌 **Depois de:** criar ou saber o nome do branch  
📌 **Antes de:** iniciar alterações no novo fluxo

</details>

---

<details>
<summary><strong>🔗 git merge</strong></summary>

Combina alterações de outro branch no branch atual.

```bash
git checkout main
git merge nova-feature
```

📝 **Usar quando:** deseja unir o trabalho de diferentes branches.

📌 **Depois de:** terminar a feature/teste em outro branch  
📌 **Antes de:** deletar branches ou fazer deploy

</details>

---

<details>
<summary><strong>🗃️ git stash</strong></summary>

Salva temporariamente alterações sem commit.

```bash
git stash         # guarda as alterações
git stash list    # mostra lista de stashes
git stash pop     # aplica e remove o stash
```

📝 **Usar quando:** precisa trocar de branch mas tem alterações não commitadas.

📌 **Depois de:** alterar arquivos mas ainda não querer commitá-los  
📌 **Antes de:** mudar de branch para não perder o progresso

❗ **Importante:** não funciona com commits já feitos!

</details>

---

<details>
<summary><strong>🧼 git reset</strong></summary>

Remove commits ou alterações da história local.

```bash
git reset --soft HEAD~1     # desfaz o commit, mantém staging
git reset --hard HEAD~1     # desfaz commit e alterações
```

📝 **Usar quando:** você cometeu um erro em um ou mais commits recentes e quer voltar atrás.

📌 **Depois de:** commits indevidos ou errados  
📌 **Antes de:** reescrever ou descartar alterações

❗ **Atenção:** `--hard` remove alterações sem chance de recuperação!

</details>

---

<details>
<summary><strong>🎯 git log</strong></summary>

Mostra o histórico de commits do projeto.

```bash
git log
git log --oneline --graph
```

📝 **Usar quando:** deseja entender o que foi feito, por quem e quando.

📌 **Depois de:** vários commits  
📌 **Antes de:** corrigir, rever ou analisar histórico

</details>

---

## 🧠 Dicas Avançadas

- Use `git diff` para ver o que mudou entre arquivos ou commits
- Combine `git stash` com `git pull` para evitar conflitos
- Prefira `git pull --rebase` para histórico linear
- Evite `git push -f` (forçado) em repositórios compartilhados

---

## 📚 Fluxo de Trabalho Recomendado

```bash
git clone <repo-url>
git checkout -b minha-feature
# faz alterações...
git add .
git commit -m "feat: adiciona nova funcionalidade"
git push origin minha-feature
# cria um pull request
```

---

## 🛟 Recuperação

| Situação                     | Solução                          |
| ---------------------------- | -------------------------------- |
| Alteração local sem commit   | `git checkout arquivo`           |
| Commit errado                | `git reset --soft HEAD~1`        |
| Arquivos perdidos após stash | `git stash apply` ou `stash pop` |
| Merge conflitante            | Edita arquivos e `git commit`    |

---

## 📦 Referência Rápida de Comandos

| Comando        | Ação                                 |
| -------------- | ------------------------------------ |
| `git init`     | Inicia um repositório local          |
| `git clone`    | Clona um repositório remoto          |
| `git add`      | Adiciona arquivos ao staging         |
| `git commit`   | Salva alterações no repositório      |
| `git status`   | Mostra o estado atual do repositório |
| `git pull`     | Atualiza com o repositório remoto    |
| `git push`     | Envia alterações para o remoto       |
| `git branch`   | Cria/lista branches                  |
| `git checkout` | Troca de branch ou commit            |
| `git merge`    | Mescla branches                      |
| `git stash`    | Guarda alterações não commitadas     |
| `git reset`    | Desfaz commits                       |
| `git log`      | Exibe o histórico de commits         |
| `git diff`     | Mostra diferenças entre arquivos     |

---

📌 _Resumo escrito por Felipe Castro — ideal para estudos de Git, entrevistas técnicas e concursos._
