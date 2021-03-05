<template>
  <v-card class="card" elevation="2" data-app>
    <img :src="pokemonInfo.sprites.front_default" alt="" />
    <br />
    <h3 class="capitalize">#{{ pokemonInfo.id }} - {{ pokemon.name }}</h3>
    <v-divider></v-divider>
    <span>|</span>
    <span class="capitalize" v-for="type in pokemonInfo.types" :key="type.slot">
      {{ type.type.name }} |
    </span>
    <v-divider></v-divider>
    <v-btn
      elevation="2"
      rounded
      x-small
      class="btn_info"
      @click="dialog = !dialog"
      >Saiba mais</v-btn
    >

    <v-dialog v-model="dialog">
      <Info
        @closeDialog="dialog = false"
        :pokemonInfo="pokemonInfo"
        :pokemonEvolution="pokemonEvolution"
      />
    </v-dialog>
  </v-card>
</template>

<script>
import api from "../../api/api";

export default {
  name: "Card",
  components: {
    Info: () => import("./Info.vue")
  },
  props: {
    pokemon: {
      type: Object,
      default: () => {}
    }
  },

  data() {
    return {
      pokemonInfo: {},
      pokemonEvolution: {},
      dialog: false
    };
  },

  methods: {
    async getPokemonInfo() {
      await api.get(this.pokemon.url).then(({ data }) => {
        this.pokemonInfo = data;
      });
    },

    getPokemonEvolution() {
      const id = this.pokemon.url
        .split("pokemon/")
        .pop()
        .slice(0, -1);
      api
        .get(`https://pokeapi.co/api/v2/evolution-chain/${id}/`)
        .then(({ data }) => {
          this.pokemonEvolution = data;
          console.log(data);
        });
    }
  },

  mounted() {
    this.getPokemonInfo();
    this.getPokemonEvolution();
  }
};
</script>

<style>
.x {
  width: 100%;
}
.info {
  text-align: left;
}
.btn_close {
  margin-left: auto;
}
.card {
  width: 25%;
  margin: 10px;
  padding: 10px;
}
.card img {
  border: 1px solid #666;
  border-radius: 5px;
}
.capitalize {
  text-transform: capitalize;
}
.btn_info {
  background-color: red !important;
  color: white !important;
}
hr {
  margin: 10px 0px;
}
</style>
