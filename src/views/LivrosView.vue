<script>
import { v4 as uuid4 } from "uuid";
export default {
  data() {
    return {
      livros: [
        {
          id: "7c9e22c2-b2f4-45ba-80d9-5d702bf357ec",
          nome: "Livro 1",
          ISBN: "5464777-378736",
          quantidade: "6000",
          preco: "19,99",
        },
        {
          id: "3dbf86f0-f4b3-436b-aae7-3a6c043547bb",
          nome: "Livro 2",
          ISBN: "5464777-378736",
          quantidade: "6000",
          preco: "19,99",
        },
        {
          id: "d53d669e-1143-48b6-8169-43156f646b24",
          nome: "Livro 3",
          ISBN: "5464777-378736",
          quantidade: "6000",
          preco: "19,99",
        },
      ],
      novo_livro: "",
      novo_ISBN: "",
      novo_quantidade: "",
      novo_preco: "",
    };
  },
  methods: {
    salvar() {
      if (this.novo_livro !== "") {
        const novo_id = uuid4();
        this.livros.push({
          id: novo_id,
          nome: this.novo_livro,
          ISBN: this.novo_ISBN,
          quantidade: this.novo_quantidade,
          preco: this.novo_preco,
        });
        this.novo_livro = "";
        this.novo_ISBN = "";
        this.novo_quantidade = "";
        this.novo_preco = "";
      }
    },
    excluir(livro) {
      const indice = this.livros.indexOf(livro);
      this.livros.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de livros</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        v-model="novo_livro"
        @keydown.enter="salvar"
        placeholder="Livro"
      />
      <input
        type="text"
        v-model="novo_ISBN"
        @keydown.enter="salvar"
        placeholder="ISBN"
      />
      <input
        type="text"
        v-model="novo_quantidade"
        @keydown.enter="salvar"
        placeholder="Quantidade"
      />
      <input
        type="text"
        v-model="novo_preco"
        @keydown.enter="salvar"
        placeholder="Preço"
      />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-livros">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>ISBN</th>
            <th>Quantidade</th>
            <th>Preço</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{ livro.id }}</td>
            <td>{{ livro.nome }}</td>
            <td>{{ livro.ISBN }}</td>
            <td>{{ livro.quantidade }}</td>
            <td>{{ livro.preco }}</td>
            <td></td>
            <td>
              <button @click="excluir(livros)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
.title {
  text-align: center;
  margin: 0rem 0;
  color: #ccc;
}

.form-input {
  display: flex;
  justify-content: center;
  margin: 2rem 0;
}

.form-input input {
  width: 50%;
  padding: 0.5rem;
  border: 1px ridge #ccc;
  border-radius: 10px;
}

.form-input button {
  padding: 0.5rem;
  border: 1px double rgb(0, 0, 0);
  border-radius: 10px;
  background-color: black;
  color: #ccc;
  font-weight: bold;
  margin-left: 1%;
}

.list-times {
  display: flex;
  justify-content: center;
}

table {
  width: 50%;
  border-collapse: collapse;
  margin: 0 auto;
  border: 1px solid black;
  font-size: 1.1rem;
  color: #ccc;
}

table thead {
  background-color: darkblue;
  color: white;
}

table tbody tr {
  text-align: center;
}

table tbody tr:nth-child(odd) {
  background-color: rgb(0, 0, 0);
}

body {
  background: rgb(2, 0, 36);
  background: linear-gradient(
    180deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(11, 9, 121, 0.8407738095238095) 40%,
    rgba(0, 212, 255, 1) 100%
  );
}
</style>
