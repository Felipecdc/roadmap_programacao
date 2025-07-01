# 🖼️ Vue.js – Framework Progressivo para Interfaces

**Vue.js** é um framework JavaScript usado para construir **interfaces de usuário (front-end)** de forma reativa, modular e eficiente.  
Ele é focado principalmente no **lado do cliente**, mas com ferramentas como **Nuxt.js**, também permite projetos full stack.

---

## 🌱 Conceitos Básicos

- É reativo: atualiza a tela automaticamente ao mudar dados.
- Usa HTML com marcações especiais (`directives`) como `v-if`, `v-for` e `v-model`.
- Separa bem os arquivos em blocos `<template>`, `<script>` e `<style>`.
- Fácil de aprender para quem já sabe HTML, CSS e JS.
- Pode ser usado tanto em projetos pequenos quanto grandes.

---

## 📦 Instalação

<details>
<summary>📌 Instalar Vue CLI</summary>

```bash
npm install -g @vue/cli
vue create meu-projeto
cd meu-projeto
npm run serve
```

</details>

<details>
<summary>📌 Ou usar Vite (mais moderno)</summary>

```bash
npm create vite@latest meu-projeto -- --template vue
cd meu-projeto
npm install
npm run dev
```

</details>

---

## 🔁 Diretivas Vue

<details>
<summary>🔁 v-if / v-else-if / v-else</summary>

**Usado para mostrar ou esconder elementos com base em condições.**

```js
<template>
  <div>
    <p v-if="idade >= 18">Você é maior de idade.</p>
    <p v-else-if="idade >= 13">Você é adolescente.</p>
    <p v-else>Você é criança.</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      idade: 15
    }
  }
}
</script>
```

</details>

<details>
<summary>🔁 v-for</summary>

**Usado para repetir um elemento para cada item de uma lista.**

```js

<template>
  <ul>
    <li v-for="(item, index) in frutas" :key="index">
      {{ index + 1 }} - {{ item }}
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      frutas: ['Maçã', 'Banana', 'Laranja']
    }
  }
}
</script>


```

</details>

<details>
<summary>🔗 v-model</summary>

**Faz ligação automática entre um input e o dado no JavaScript.**

```js

<template>
  <div>
    <input v-model="nome" placeholder="Digite seu nome" />
    <p>Olá, {{ nome }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nome: ''
    }
  }
}
</script>

```

</details>

<details>
<summary>🔗 v-bind</summary>

**Liga atributos HTML a valores dinâmicos. Usa-se `:` como atalho.**

```js
<template>
  <img :src="imagem" :alt="descricao" />
</template>

<script>
export default {
  data() {
    return {
      imagem: 'https://via.placeholder.com/150',
      descricao: 'Imagem de exemplo'
    }
  }
}
</script>
```

</details>

<details>
<summary>⚡ v-on</summary>

**Escuta eventos como `click`, `input`, `submit` etc. Atalho: `@evento`.**

```js
<template>
  <button @click="mostrarAlerta">Clique aqui</button>
</template>

<script>
export default {
  methods: {
    mostrarAlerta() {
      alert('Você clicou no botão!')
    }
  }
}
</script>

```

</details>

<details>
<summary>👁️ v-show</summary>

**Semelhante ao `v-if`, mas o elemento sempre está no DOM — só muda o `display`.**

```js
<template>
  <div>
    <p v-show="mostrar">Esse texto aparece se 'mostrar' for true.</p>
    <button @click="mostrar = !mostrar">Alternar</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mostrar: true
    }
  }
}
</script>

```

- 🔎 Use v-if quando quiser remover do DOM.
- ✅ Use v-show quando só quiser esconder/mostrar rápido.

</details>

<details>
<summary>🧩 v-slot</summary>

**Permite passar conteúdo para um componente filho via "slot" (como se fosse um "buraco" para preencher).**

```js
<!-- ComponentePai.vue -->
<template>
  <MeuCard>
    <template v-slot:titulo>
      <h2>Slot Título</h2>
    </template>
    <template v-slot:conteudo>
      <p>Este conteúdo foi inserido no slot.</p>
    </template>
  </MeuCard>
</template>
```

```js
<!-- MeuCard.vue -->
<template>
  <div class="card">
    <header>
      <slot name="titulo"></slot>
    </header>
    <main>
      <slot name="conteudo"></slot>
    </main>
  </div>
</template>
```

🧠 Muito útil para criar componentes reutilizáveis com conteúdo flexível.

</details>

<details>
<summary>🔗 ref</summary>

**Permite acessar um elemento ou componente diretamente no JavaScript.**

```js
<template>
  <input ref="meuInput" placeholder="Clique no botão para focar" />
  <button @click="focar">Focar no input</button>
</template>

<script>
export default {
  methods: {
    focar() {
      this.$refs.meuInput.focus()
    }
  }
}
</script>

```

💡 Ideal para manipulações diretas de DOM ou foco.

</details>

<details>
<summary>🧠 computed</summary>

**São propriedades que dependem de outras e são automaticamente recalculadas.**

```js
<template>
  <div>
    <p>{{ nomeCompleto }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nome: 'Felipe',
      sobrenome: 'Castro'
    }
  },
  computed: {
    nomeCompleto() {
      return this.nome + ' ' + this.sobrenome
    }
  }
}
</script>
```

⚡ Mais eficientes que funções em templates, pois são cacheadas.

</details>

<details>
<summary>🛠️ methods</summary>

**Funções que são chamadas por eventos ou diretamente no código.**

```js
<template>
  <button @click="dizerOi">Clique aqui</button>
</template>

<script>
export default {
  methods: {
    dizerOi() {
      alert('Oi!')
    }
  }
}
</script>

```

🔧 Use `methods` para ações. Use `computed` para dados derivados.

</details>

<details>
<summary>📡 watch</summary>

\*_Observa mudanças em dados e executa algo sempre que eles mudam._

```js
<template>
  <input v-model="busca" placeholder="Digite para buscar..." />
</template>

<script>
export default {
  data() {
    return {
      busca: ''
    }
  },
  watch: {
    busca(novoValor) {
      console.log('Buscando por:', novoValor)
    }
  }
}
</script>


```

🔍 Perfeito para chamadas de API, validações ou efeitos colaterais.

</details>

<details>
<summary>🚀 Nova Sintaxe do Vue 3 – <code>&lt;script setup&gt;</code> e <code>&lt;style scoped&gt;</code></summary>

O Vue 3 trouxe uma forma mais simples e moderna de escrever componentes usando <code>&lt;script setup&gt;</code>.  
Este formato torna o código mais limpo e direto, sem precisar declarar explicitamente a função `setup()`

Além disso, o <code>&lt;style scoped&gt;</code> garante que o CSS do componente só afete aquele componente, evitando vazamento de estilos para outras partes da aplicação.

```js
<template>
  <div>
    <h2>{{ titulo }}</h2>
    <button @click="contador++">Cliquei {{ contador }} {{ contador === 1 ? 'vez' : 'vezes'}}</button>
  </div>
</template>

<script setup>
import { ref } from "vue";

const titulo = "Meu Componente";
const contador = ref(0);
</script>

<style scoped>
button {
  background-color: #333;
  color: white;
  padding: 10px;
  border: none;
  border-radius: 8px;
}
</style>
```

🔍 Perfeito para chamadas de API, validações ou efeitos colaterais.

</details>

---

## 🧠 Sintaxe Básica

<details>
<summary>📄 Exemplo de componente Vue</summary>

```javascript
<template>
  <div>
    <h1>{{ titulo }}</h1>
    <input v-model="nome" placeholder="Digite seu nome" />
    <p v-if="nome">Olá, {{ nome }}!</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titulo: "Meu App Vue",
      nome: "",
    };
  },
};
</script>

<style>
h1 {
  color: green;
}
</style>
```

</details>

---

## 🛠️ Comandos Comuns

<details> 
<summary>📌 Comandos do projeto</summary>

```javascript
npm run dev        # Inicia o servidor de desenvolvimento
npm run build      # Gera os arquivos para produção
npm run lint       # Verifica e corrige problemas no código
```

</details>

<details> 
<summary>📌 Comandos úteis do Vue CLI</summary>

```javascript
vue create projeto         # Cria novo projeto com Vue CLI
vue add router             # Adiciona Vue Router (rotas)
vue add vuex               # Adiciona Vuex (estado global)

```

</details>

---

## 🌐 Vue pode ser usado como Front e Back?

- Vue **por padrão é front-end**. Ele controla a interface do usuário.
- Para **back-end ou SSR (renderização no servidor)**, você pode usar o **Nuxt.js**, que é baseado em Vue.
- Com o Nuxt, você pode criar APIs, autenticação, rotas e tudo do lado do servidor, parecido com o Next.js do React.

---

## 🧪 Testes no Vue

- **Vitest** – para testes unitários modernos com suporte ao Vite
- **Vue Test Utils** – biblioteca oficial para testar componentes Vue
- **Cypress** – para testes end-to-end no navegador

---

## 📚 EcoSistema Vue

- **Pinia**: substituto moderno e mais simples para o Vuex (controle de estado global)
- **Vue Router**: sistema de rotas para navegação
- **Nuxt.js**: framework fullstack com Vue
- **Vite**: empacotador rápido e moderno (melhor que Webpack)
- **Quasar / Vuetify / PrimeVue**: bibliotecas de componentes prontos

📌 _Resumo escrito por Felipe Castro — voltado para estudos e concursos na área de Desenvolvimento Web._
