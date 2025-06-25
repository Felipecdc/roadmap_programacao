# 🧱 Programação Orientada a Objetos (POO)

A **Programação Orientada a Objetos** é um paradigma que cria objetos reutilizáveis e define claramente o que eles são e o que fazem, facilitando a organização e manutenção do código.

---

## 🏗️ Classes

Uma **classe** é um modelo que define a estrutura (atributos) e comportamento (métodos) de um objeto.

<details>
  <summary>📌 Exemplo de classe em JavaScript</summary>

```javascript
// Modelo (objeto)
class Pessoa {
  constructor(nome, idade) {
    this.nome = nome; // Atributo (variáveis)
    this.idade = idade; // Atributo (variáveis)
  }

  // Método (função)
  falar() {
    console.log(`Olá, meu nome é ${this.nome}`);
  }
}
```

</details>

---

## 📦 Atributos

São as **variáveis internas** que armazenam o estado do objeto.

<details>
  <summary>💬 Explicação</summary>

Os atributos representam as características de um objeto. Por exemplo, numa classe Pessoa, atributos podem ser `nome` e `idade`.

</details>

---

## ⚙️ Métodos

São **funções dentro da classe** que definem comportamentos dos objetos.

<details>
  <summary>📌 Exemplo de método</summary>

```javascript
falar() {
  console.log(`Olá, meu nome é ${this.nome}`);
}
```

</details>

---

## 🌳 Herança

Permite que uma classe **herde atributos e métodos de outra classe**, promovendo reutilização.

<details>
  <summary>📌 Exemplo de herança</summary>

```javascript
class Animal {
  comer() {
    console.log("Comendo...");
  }
}

class Cachorro extends Animal {
  latir() {
    console.log("Au Au!");
  }
}

const dog = new Cachorro();
dog.comer(); // herdado da classe Animal
dog.latir(); // próprio da classe Cachorro
```

</details>

---

## 🔄 Polimorfismo

Permite utilizar um **método de outra class de formas diferentes** dependendo do objeto.

<details>
  <summary>💬 Explicação</summary>

```javascript
class Hardware {
  ligar() {
    console.log("Ligando o sistema genérico.");
  }
}

class Laptop extends Hardware {
  ligar() {
    console.log("Pressionando o botão de ligar o laptop.");
  }
}

class Carro extends Hardware {
  ligar() {
    console.log("Girando a chave para ligar o carro.");
  }
}

const carro = new Carro();
const laptop = new Laptop();

// Função genérica que executa a ação de ligar
function executarLigacao(dispositivo) {
  dispositivo.ligar();
}

executarLigacao(carro); // Saída: Girando a chave para ligar o carro.
executarLigacao(laptop); // Saída: Pressionando o botão de ligar o laptop.
```

</details>

---

## 🔐 Encapsulamento

É uma característica de segurança, onde deve permanecer escondido dentro da class o que não pode ser modificado fora dela, expondo apenas o necessário por meio de métodos publicos.

<details>
  <summary>💬 Explicação</summary>

Geralmente feito com atributos privados e métodos `get` e `set`.

```javascript
class ContaBancaria {
  #saldo = 0; // atributo privado

  depositar(valor) {
    if (valor > 0) {
      this.#saldo += valor;
    }
  }

  consultarSaldo() {
    return this.#saldo;
  }
}

const conta = new ContaBancaria();
conta.depositar(100);
console.log(conta.consultarSaldo()); // 100
console.log(conta.#saldo); // ❌ Erro: não é acessível diretamente
```

</details>

---

## 🎯 Abstração

Consiste em simplificar a complexidade do sistema, expondo apenas o necessário e escondendo detalhes internos.

<details>
  <summary>💬 Explicação</summary>

```javascript
class Mecanico {
  // Atributos privados que representam partes internas do carro
  #motor;
  #biela;
  #corrente;
  #valvula;

  constructor(erroReportado) {
    this.#diagnosticar(erroReportado);
  }

  // Método privado que simula o diagnóstico e a manutenção
  #diagnosticar(erro) {
    // Lógica complexa
    this.#motor = "trocado"; // Importante o cliente saber
    this.#biela = "ok"; // Detalhe técnico irrelevante
    this.#corrente = "ajustada"; // Detalhe técnico irrelevante
    this.#valvula = "substituída"; // Importante o cliente saber
  }

  // Método público que retorna apenas as informações relevantes ao cliente
  retornaResumo() {
    return {
      valor: 1200,
      pecasTrocadas: ["motor", "valvula"], // Apenas o essencial é mostrado
      resumo: "Foram trocadas peças com defeito e ajustado o sistema interno.",
    };
  }
}

// Exemplo de uso
const mecanico = new Mecanico("barulho estranho");
console.log(mecanico.retornaResumo());
```

</details>

---

📌 _Resumo escrito por Felipe Castro — ideal para estudos e concursos._
