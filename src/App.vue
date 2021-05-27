<template>
  <div id="app">
    <Header 
      @search="search" 
    />

    <Main 
      v-if="results.movie.length > 0" 
      type="movie" 
      :list="results.movie" 
    />

    <Main 
      v-if="results.tv.length > 0" 
      type="tv" 
      :list="results.tv" 
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
      apiURL: "https://api.themoviedb.org/3/search/",
      apiKey: "8aba2f0fc3e09fb1de7523aaaf3513bc",
      query: "",
      results: {
        // array movies
        movie: [],
         // array tv
        tv: [],
      },
    };
  },
  methods: {
    // funzione che richiama la funzione searching in movie e in tv
    search(obj) {
      if (obj.type === "all") {
        this.searching(obj.text, "movie");
        this.searching(obj.text, "tv");
      }
    },
    // funzione che permette di eseguire la chiamata API avviando la ricerca di query(del testo inserito dall'utente)
    searching(query, type) {
      if (query != "") {
        this.query = query;
        // console.log(query);
        axios
          .get(this.apiURL + type, {
            params: {
              api_key: this.apiKey,
              query: this.query,
              language: "it-IT",
            },
          })
          .then((resp) => {
            this.results[type] = resp.data.results;
            console.log(this.results);
          })
          .catch((error) => {
            console.log(error);
          });
      }
    },
  },
};
</script>

<style lang="scss">
// importo il foglio di stile general.scss
@import "@/assets/style/general";
</style>
