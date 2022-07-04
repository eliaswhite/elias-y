<script>
import { v4 as uuid4 } from "uuid";
export default {
  data() {
    return {
      autores: [
        {
          id: "7c9e22c2-b2f4-45ba-80d9-5d702bf357ec",
          nome: "Autor 1",
        },
        {
          id: "3dbf86f0-f4b3-436b-aae7-3a6c043547bb",
          nome: "Autor 2",
        },
        {
          id: "d53d669e-1143-48b6-8169-43156f646b24",
          nome: "Autor 3",
        },
      ],
      novo_autor: "",
    };
  },
  methods: {
    salvar() {
      if (this.novo_autor !== "") {
        const novo_id = uuid4();
        this.autores.push({
          id: novo_id,
          nome: this.novo_autor,
        });
        this.novo_autor = "";
      }
    },
    excluir(autor) {
      const indice = this.autores.indexOf(autor);
      this.autores.splice(indice, 1);
    },
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Gerenciamento de autores</h2>
    </div>
    <div class="form-input">
      <input
        type="text"
        v-model="novo_autor"
        @keydown.enter="salvar"
        placeholder="Autor"
      />
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-autores">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="autor in autores" :key="autor.id">
            <td>{{ autor.id }}</td>
            <td>{{ autor.nome }}</td>
            <td>
              <button @click="excluir(autor)">Excluir</button>
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
  border: 1px double rgb(72, 255, 0);
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
}

table thead {
  background-color: darkblue;
  color: white;
}

table tbody tr {
  text-align: center;
}

table tbody tr:nth-child(odd) {
  background-color: cadetblue;
}
</style>
