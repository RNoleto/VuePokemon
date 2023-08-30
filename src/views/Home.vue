<template>
  <h1>Pagina Home</h1>
  <h3>Fazendo requisição HTTP com o Axios</h3>
  <div v-for="(pokemon,index) in pokemons" :key="index">
  <p>{{ pokemon.name }}</p>
  </div>
</template>
<script lang="ts">
import { defineComponent, onMounted, ref } from 'vue';
import api from "../services/api";
export default defineComponent({
  name: "Home",
  setup() {
    const pokemons = ref([]);
    const fetchPokemons =  () => api.get("/pokemon?limit=20").then((response => pokemons.value = response.data.results ));

    onMounted(fetchPokemons);

    return { pokemons };
  },
});
</script>