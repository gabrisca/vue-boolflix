<template>
  <main class="container">
    <!-- inserisco il titolo in base al type -->
    <h1 class="text-center mt-3 mb-3">{{ titles[type] }}</h1>
    <div class="row d-flex justify-content-center mt-5 mb-5">
    <Card 
      v-for="card in list" 
      :key="card.id" 
      :card="card" 
    />
    </div>
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