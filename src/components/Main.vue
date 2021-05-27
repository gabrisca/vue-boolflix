<template>
  <main class="container mt-5 mb-5">
    <h1 class="text-center mb-3">{{ titles[type] }}</h1>
    <Card 
      v-for="card in list" 
      :key="card.id" 
      :card="card" 
    />
  </main>
</template>

<script>
import Card from "./Card.vue";

export default {
  components: { Card },
  name: "Main",
  props: { // props mette in comunicazione Main con il genitore App
    type: String, // Main riceve type che è una stringa 
    list: Array, // Main riceve list che è un Array da ciclare
  },
  data() {
    return {
      titles: {
        movie: "Movies",
        tv: "TV Series",
      },
    };
  },
};
</script>

<style lang='scss' scoped>
</style>