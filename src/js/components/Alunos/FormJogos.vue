<template>
  <form id="form-games" v-on:submit.prevent="onSubmit">
    <h2>Cadastrar Jogo</h2>
    <p>
      <label for="title">Título:</label>
      <input name="title" v-model="title" />
    </p>
    <p>
      <label for="price">Preço:</label>
      <input name="price" v-model="price" type="number" />
    </p>
    <p>
      <label for="platform">Plataforma:</label>
      <input name="platform" v-model="platform" />
    </p>
    <p>
      <label for="image">Link da capa do jogo:</label>
      <input name="image" v-model="image" />
    </p>
    <p>
      <label for="totalAvailable">Total disponível:</label>
      <input name="totalAvailable" v-model="totalAvailable" type="number" />
    </p>
    
      <div class="error">{{errorMessage}}</div>
      <input type="submit" value="Salvar" />
    
  </form>
</template>

<script>
import Game from '../../models/Game';

export default {
  data() {
    return {
      errorMessage: "",
      id: "",
      title: "",
      price: "",
      platform: "",
      image: "",
      totalAvailable: ""
    };
  },
  methods: {
    onSubmit(e) {
      this.errorMessage = "";
      if (!this.title) {
        this.errorMessage = "Nome é obrigatório"
        return;
      }
      const game = new Game(this.id, this.title, this.price, this.platform, this.image, this.totalAvailable);
      this.$parent.salvar(game);
      this.id = 0;
      this.title = '';
      this.price = '';
      this.platform = '';
      this.image = '';
      this.totalAvailable = '';
    },
    carregar(game) {
      this.id = game.id;
      this.title = game.title;
      this.price = game.price;
      this.platform = game.platform;
      this.image = game.image;
      this.totalAvailable = game.totalAvailable;
    }
  }
};
</script>

<style>
.error {
  color: red;
}

#form-games {
  border: 1px solid #aaa;
  padding: 10px;
}
label {
  display: block;
}
</style>
