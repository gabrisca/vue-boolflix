<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import axios from 'axios'
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  components: { 
    Header, 
    Main 
  },
  data(){
    return{
      apiURL:"https://api.themoviedb.org/3/search/movie",
      apiKey: "8aba2f0fc3e09fb1de7523aaaf3513bc",
      // ricordati il v-model stringa vuota
      query: "ritorno al futuro"
    }
  },
  created() {
    axios.get(this.apiUrl, {
      params: {
        api_Key: this.apiKey,
        query: this.query,
        language: 'it-IT'
      }
    })
    .then((resp)=>{
      console.log(resp.data.results);
    })
    .catch((error)=>{
      console.log(error);
    })
  },
}

</script>

<style lang="scss">
// importo il foglio di stile general.scss
@import "@/assets/style/general";
</style>
