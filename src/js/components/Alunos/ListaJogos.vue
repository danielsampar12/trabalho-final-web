<template>
  <div>
    <h2>Lista de Jogos</h2>
    <table>
      <thead>
        <tr>
          <th>#</th>
          <th>Titulo</th>
          <th>Preço</th>
          <th>Plataforma</th>
          <th>Imagem</th>
          <th>Total Disponível</th>

          <th>Ações</th>
        </tr>
      </thead>
      <tbody>
        <tr v-if="!possuiJogos">
          <td colspan="4">Nenhum registro encontrado</td>
        </tr>
        <tr v-for="game in games" v-bind:key="game.id">
          <td>{{game.id}}</td>
          <td>{{game.title}}</td>
          <td>{{game.price}}</td>
          <td>{{game.platform}}</td>
          <td><img v-bind:src="game.image"></td>
          <td>{{game.totalAvailable}}</td>
          <td>
            <a href="#" v-on:click.prevent="editar(game)">editar</a> |
            <a href="#" v-on:click.prevent="excluir(game.id)">excluir</a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  computed: {
    possuiJogos() {
      return this.games && this.games.length > 0;
    }
  },
  methods: {
    editar(game) {
      this.$parent.carregar(game);
    },
    excluir(id) {
      if (confirm("Deseja realmente excluir o aluno?")) {
        this.$parent.excluir(id);
      }
    }
  },
  props: { games: Array }
};
</script>

<style scoped>
table {
  border-collapse: collapse;
  width: 100%;
}
th {
  background: black;
  color: white;
}
td,
th {
  border: 1px solid #ddd;
  padding: 8px;
}
tr:nth-child(even) {
  background: #ddd;
}
tr:hover {
  background-color: #aaa;
}
img {
  max-width: 90px;
}
</style>
