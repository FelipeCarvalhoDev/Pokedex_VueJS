<template>
  <v-card class="info" elevation="2">
    <v-card-title
      ><h3 class="capitalize">{{ pokemonInfo.name }}</h3>
      <v-btn class="btn_close" icon @click="closeDialog">
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </v-card-title>
    <v-divider></v-divider>
    <v-card-text>
      <strong>Evolução:</strong>
      <br />
      <span>|</span>
      <span
        class="capitalize"
        v-for="evolution in pokemonEvolution.chain.evolves_to"
        :key="evolution.species.name"
      >
        {{ evolution.species.name }} |
      </span>
    </v-card-text>

    <v-card-text>
      <strong>Habilidades:</strong>
      <br />
      <span>|</span>
      <span
        class="capitalize"
        v-for="ability in pokemonInfo.abilities"
        :key="ability.ability.name"
      >
        {{ ability.ability.name }} |
      </span>
    </v-card-text>

    <v-card-text>
      <strong>Movimentos:</strong>
      <br />
      <span>|</span>
      <span
        class="capitalize"
        v-for="move in pokemonInfo.moves"
        :key="move.move.name"
      >
        {{ move.move.name }} |
      </span>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "Info",
  props: {
    pokemonInfo: {
      type: Object,
      default: () => {}
    },
    pokemonEvolution: {
      type: Object,
      default: () => {}
    }
  },
  methods: {
    closeDialog() {
      this.$emit("closeDialog");
    }
  },
  mounted() {
    console.log(this.pokemonName);
    console.log(this.pokemonEvolution);
  }
};
</script>

<style>
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
