<template>
  <div>
    {{ pokemons }}
  </div>
</template>

<script>
import api from '../../api/api';

export default {
  name: 'Pokedex',
  props: {
    msg: String
  },
  
  data() {
    return {
      pokemons: []
    }
  },

  methods: {
    async getPokemon() {
      await api.get("api/v2/pokemon").then();    
    }
  },

  async mounted() {
    await this.getPokemon()
    this.pokemons = this.getPokemon();
    console.log(this.pokemons)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
