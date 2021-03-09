<template>
  <div class="pokedex">
    <v-app>
      <div class="filter">
        <FilterPokemon
          class="form"
          @setInitialPokemon="setInitialPokemon"
          @setFinalPokemon="setFinalPokemon"
        />
      </div>
      <v-divider></v-divider>
      <div class="results">
        <Card
          v-for="pokemon in pokemons"
          :key="pokemon.name"
          :pokemon="pokemon"
        />
      </div>
    </v-app>
  </div>
</template>

<script>
import api from "../../api/api";

export default {
  name: "Pokedex",
  components: {
    Card: () => import("./Card.vue"),
    FilterPokemon: () => import("./FilterPokemon.vue")
  },

  data() {
    return {
      pokemons: [],
      initialPokemon: 2,
      finalPokemon: 5
    };
  },

  methods: {
    setInitialPokemon(initial) {
      console.log(initial);
      this.initialPokemon = initial;
    },
    setFinalPokemon(final) {
      console.log(final);
      this.finalPokemon = final;
    },
    getPokemon() {
      api
        .get(
          `api/v2/pokemon/?limit=${this.finalPokemon -
            this.initialPokemon +
            1}&offset=${this.initialPokemon - 1}`
        )
        .then(({ data }) => {
          this.pokemons = [...data.results];
        });
    }
  },

  mounted() {
    this.getPokemon();
  },

  watch: {
    initialPokemon() {
      this.getPokemon();
    },
    finalPokemon() {
      this.getPokemon();
    }
  }
};
</script>

<style scoped>
.v-application {
  background: none !important;
}
.pokedex {
  margin: auto;
  max-width: 90%;
}
.results {
  display: flex;
  flex-wrap: wrap;
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
hr {
  margin: 20px 0 10px 0;
}
</style>
