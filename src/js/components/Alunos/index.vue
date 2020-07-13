<template>
  <div>
    <FormJogos ref="FormJogos"></FormJogos>
    <ListaJogos v-bind:games="games"></ListaJogos>
  </div>
</template>

<script>
import FormJogos from "./FormJogos.vue";
import ListaJogos from "./ListaJogos.vue";
import Game from "../../models/Game";

export default {
  data() {
    return {
      proxId: 6,
      games: [
        new Game(1, 'God Of War', 250, 'PS4', 'https://images-na.ssl-images-amazon.com/images/I/81gXqxyFrxL.jpg', 10),
        new Game(2, 'Destiny', 0, 'PS4', 'https://images-americanas.b2w.io/produtos/01/00/item/132474/0/132474064_1GG.jpg', 100000),
        new Game(3, 'Fifa20', 250, 'PS4 e XBox One', 'https://media.playstation.com/is/image/SCEA/ea-sports-fifa-20-listing-thumb-01-ps4-us-13aug19?$facebook$', 10),
        new Game(4, 'God Of War', 250, 'PS4', '', 10),
        new Game(5, 'God Of War', 250, 'PS4', '', 10),

       
      ]
    };
  },
  methods: {
    carregar(game) {
      this.$refs.FormAlunos.carregar(game);
    },
    salvar(game) {
      if (game.id) {
        const index = this.games.findIndex(x => x.id == game.id);
        const games = [...this.games]; //cria copia de alunos
        games[index] = game; //edita o aluno pelo indice
        this.games = games; //atualiza this.alunos
      }
      else {
        game.id = this.proxId;
        this.proxId++;
        this.games.push(game);
      }
    },
    excluir(id) {
      const index = this.games.findIndex(x => x.id==id);
      this.games.splice(index, 1);
    }
  },
  components: {
    FormJogos,
    ListaJogos
  }
};
</script>

<style>
</style>
