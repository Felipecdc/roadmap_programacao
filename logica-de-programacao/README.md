# 📚 Lógica de Programação

Lógica de programação é o **raciocínio usado para criar algoritmos** que resolvem problemas por meio de instruções, operações sequenciais, decisões e repetições.

---

## 🔢 Algoritmos

Um **algoritmo** é uma sequência finita de instruções lógicas para resolver problemas e realizar tarefas.  
Ele pode ser representado por:

- 🧠 **Pseudocódigo** – uma linguagem informal que descreve os passos do algoritmo.
- 🗺️ **Fluxograma** – uma representação gráfica das etapas do processo.

### Exemplos

<details>
<summary>Exemplo de Pseudocódigo – Verificar se número é par ou ímpar</summary>

```plaintext
Início
  Ler número
  Se número % 2 == 0 então
    Escrever "Número é par"
  Senão
    Escrever "Número é ímpar"
Fim
```

</details>

---

<details>
<summary>Exemplo de Algoritmo em Código – Python</summary>

```py
numero = int(input("Digite um número: "))

if numero % 2 == 0:
    print("Número é par")
else:
    print("Número é ímpar")

```

</details>

---

## 📊 Fluxogramas

Fluxogramas são **representações gráficas de algoritmos**, usando símbolos padronizados como:

- 🔷 **Início/Fim** – elipses
- 🟩 **Processos** – retângulos
- 🔺 **Decisões** – losangos
- 🔀 **Setas** – fluxo de execução

> Eles facilitam a visualização da lógica antes da implementação no código.

### Exemplos

<details>
<summary>Exemplo de Fluxograma – Verificar idade para votar</summary>

```plaintext
         🔷 Início
             ↓
        🟩 Ler idade
             ↓
      🔺 Idade ≥ 16?
         /       \
       Sim       Não
       ↓          ↓
🟩 Pode votar   🟩 Não pode votar
       ↓          ↓
          🔷 Fim


```

</details>

---

## 🐞 Depuração

**Depuração** é o processo de identificar e corrigir erros no código.

Ferramentas e técnicas comuns:

- ⛔ **Breakpoints**
- 📋 **Logs**
- ✅ **Testes manuais ou automatizados**

> Uma boa prática é testar pequenos blocos de código por vez.

### Exemplos

<details>
<summary>Exemplo de uso de print (log) para depuração – Python</summary>

```py
def soma(a, b):
    print(f"Somando {a} + {b}")  # log
    return a + b

resultado = soma(5, 3)
print("Resultado:", resultado)

```

</details>

---

<details>
<summary>Exemplo de uso de breakpoint – JavaScript </summary>

```javascript
function verificarIdade(idade) {
  debugger; // pausa a execução se o DevTools estiver aberto
  if (idade >= 18) {
    return "Maior de idade";
  } else {
    return "Menor de idade";
  }
}
```

### 🔧 DevTools:

É um conjunto de ferramentas de desenvolvedor embutido no navegador, usado para inspecionar código, ver logs e depurar JavaScript. `(ctrl + F12)`

No exemplo acima, o comando debugger; faz com que o navegador pause a execução nesse ponto caso o DevTools esteja aberto, permitindo ao desenvolvedor inspecionar variáveis e o fluxo do código antes de continuar.

</details>

---

## 🧠 Dica

> “Pensar como um computador” ajuda a criar algoritmos eficientes e claros.

---

📌 _Estudo criado por Felipe Castro. Última atualização: junho de 2025._
