<template>
  <div id="app">
    <h1>Lista de Produtos</h1>

    <div class="formulario">
      <h2>Cadastrar Produto</h2>

      <input
        v-model="novoProduto.nome"
        type="text"
        placeholder="Nome do produto"
      />

      <input
        v-model="novoProduto.descricao"
        type="text"
        placeholder="Descrição do produto"
      />

      <input
        v-model.number="novoProduto.preco"
        type="number"
        step="0.01"
        placeholder="Preço"
      />

      <button @click="cadastrarProduto">
        Cadastrar
      </button>
    </div>

    <div class="produtos">
      <h2>Produtos cadastrados</h2>

      <div
        v-for="(produto, index) in produtos"
        :key="index"
        class="produto"
      >
        <h3>{{ produto.nome }}</h3>
        <p>{{ produto.descricao }}</p>
        <strong>R$ {{ produto.preco.toFixed(2) }}</strong>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",

  data() {
    return {
      produtos: [
        {
          nome: "Notebook",
          descricao: "Notebook com 8GB de RAM e SSD de 256GB.",
          preco: 2500.00
        },
        {
          nome: "Smartphone",
          descricao: "Smartphone com tela de 6,5 polegadas e 128GB de armazenamento.",
          preco: 1800.00
        }
      ],

      novoProduto: {
        nome: "",
        descricao: "",
        preco: null
      }
    };
  },

  methods: {
    cadastrarProduto() {
      if (
        !this.novoProduto.nome ||
        !this.novoProduto.descricao ||
        this.novoProduto.preco === null ||
        this.novoProduto.preco === ""
      ) {
        alert("Preencha todos os campos.");
        return;
      }

      this.produtos.push({
        nome: this.novoProduto.nome,
        descricao: this.novoProduto.descricao,
        preco: Number(this.novoProduto.preco)
      });

      // Limpa o formulário após o cadastro
      this.novoProduto = {
        nome: "",
        descricao: "",
        preco: null
      };
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background-color: #f4f4f4;
}

#app {
  max-width: 800px;
  margin: 40px auto;
  padding: 20px;
}

h1 {
  text-align: center;
  color: #333;
}

.formulario {
  background: white;
  padding: 20px;
  border-radius: 8px;
  margin-bottom: 30px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.formulario input {
  display: block;
  width: 100%;
  padding: 10px;
  margin-bottom: 12px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.formulario button {
  padding: 10px 20px;
  background-color: #42b883;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.formulario button:hover {
  background-color: #369c6d;
}

.produto {
  background: white;
  padding: 20px;
  margin-bottom: 15px;
  border-radius: 8px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.produto h3 {
  margin-top: 0;
  color: #42b883;
}

.produto p {
  color: #555;
}

.produto strong {
  color: #222;
  font-size: 18px;
}
</style>
