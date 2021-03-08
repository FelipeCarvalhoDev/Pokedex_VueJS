<template>
  <div class="pokedex">
    <Filter :pokemon="pokemon" />
    <Card v-for="pokemon in pokemons" :key="pokemon.name" :pokemon="pokemon" />
  </div>
</template>

<script>
import api from "../../api/api";

export default {
  name: "Pokedex",
  components: {
    Card: () => import("./Card.vue"),
    Filter: () => import("./Filter.vue")
  },

  data() {
    return {
      pokemons: []
    };
  },

  methods: {
    getPokemon() {
      api.get("api/v2/pokemon/?limit=3&offset=0").then(({ data }) => {
        this.pokemons = [...data.results];
      });
    }
  },

  mounted() {
    this.getPokemon();
  }
};
</script>

<style scoped>
.pokedex {
  display: flex;
  flex-wrap: wrap;
  margin: auto;
  max-width: 90%;
  justify-content: center;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
