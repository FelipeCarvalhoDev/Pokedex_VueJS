<template>
  <v-form>
    <v-text-field
      label="Número Inicial"
      v-model="initialPokemon"
      @change="setInitialPokemon"
    >
    </v-text-field>
    <v-text-field
      label="Número Final"
      v-model="finalPokemon"
      @change="setFinalPokemon"
    ></v-text-field>
    <v-select
      v-model="selectedItem"
      :items="items"
      label="Pokémons por página"
    ></v-select>
    <v-select label="Visualização"></v-select>
    <v-btn elevation="2" rounded class="btn_filter">Filtrar</v-btn>
  </v-form>
</template>

<script>
// import api from "../../api/api";

export default {
  name: "FilterPokemon",
  props: {},

  data() {
    return {
      items: [10, 20, 30],
      selectedItem: "",
      initialPokemon: null,
      finalPokemon: null
    };
  },

  methods: {
    setInitialPokemon() {
      this.$emit("setInitialPokemon", this.initialPokemon);
    },
    setFinalPokemon() {
      this.$emit("setFinalPokemon", this.finalPokemon);
    }
  },

  mounted() {}
};
</script>

<style>
.form {
  display: flex;
}
.form {
  background-color: white;
  padding: 10px 20px;
  border-radius: 15px;
  align-items: center;
}
.form .v-input {
  margin: 20px 20px 0px 20px;
}
.btn_filter {
  background-color: red !important;
  color: yellow !important;
}
</style>
