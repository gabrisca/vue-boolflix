<template>
  <div id="app">
    <Header 
     @search="this.searching"
    />
    <!-- :movie viene preso dalle props di Main -->
    <!-- movies è il mio array di riferimento -->
    <Main 
      v-for="movie in movies" 
      :key="movie.id" 
      :movie="movie" 
    />
  </div>
</template>

<script>
// importo in app...
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  // dichiaro i componenti esportati in APP
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiURL: "https://api.themoviedb.org/3/search/movie",
      apiKey: "8aba2f0fc3e09fb1de7523aaaf3513bc",
      query: "",
      // array movies 
      movies: [],
    };
  },
  methods: {
    // funzione che permette di eseguire la chiamata API avviando la ricerca di query(del testo inserito dall'utente)
    searching(query) {
      this.query = query;
      // console.log(query);
      axios
        .get(this.apiURL, {
          params: {
            api_key: this.apiKey,
            query: this.query,
            language: "it-IT",
          },
        })
        .then((resp) => {
          this.movies = resp.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style lang="scss">
// importo il foglio di stile general.scss
@import "@/assets/style/general";
</style>
