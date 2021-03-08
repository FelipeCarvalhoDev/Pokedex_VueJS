<template>
  <v-form>
    <v-text-field label="Número Inicial"></v-text-field>
    <v-text-field label="Número Final"></v-text-field>
    <v-select label="Pokémons por página"></v-select>
    <v-select label="Visualização"></v-select>
    <v-btn elevation="2" rounded x-small class="btn_filter">Filtrar</v-btn>
  </v-form>
</template>

<script>
// import api from "../../api/api";

export default {
  name: "Filter",
  props: {
    pokemon: {
      type: Object,
      default: () => {}
    }
  },

  data() {
    return {};
  },

  methods: {},

  mounted() {
    console.log("Teste");
  }
};
</script>

<style>
.btn_filter {
  background-color: yellow;
}
</style>
