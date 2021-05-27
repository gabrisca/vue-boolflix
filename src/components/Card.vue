<template>
    <ul class="col-sm-6 col-md-3 col-lg-2 m-3 p-sm-2 p-md-3">
      <li>
        <span>Title: </span>
         <!-- a secoda che si cerchi un film o una serie tv inserisco entrambi i percorsi da visualizzare.
        film e serie tv hanno campi di risposta differenti (title e name) 
        Utilizzo un 'or logico ||'-->
        <h2>{{ card.title || card.name }}</h2>
      </li>
      <li>
        <span>Original Title: </span>
        <!-- a secoda che si cerchi un film o una serie tv inserisco entrambi i percorsi da visualizzare.
        film e serie tv hanno campi di risposta differenti (original_title e original_name) 
        Utilizzo un 'or logico ||'-->
        <h3>{{ card.original_title || card.original_name }}</h3>
      </li>
      <li>
        <span class="d-block">Original Language: </span>
        <h4 class="d-inline">{{ card.original_language }}</h4>
        <!-- se original_language è uguale a 'en' o 'it' aggiungo l'immagine di una bandierina -->
        <!-- binding di src che concatena il percorso dell'immagine + original_language + estensione immagine-->
        <!-- img-fluid rende responsive l'immagine -->
        <img 
          v-if="card.original_language === 'en' || card.original_language === 'it'" 
          :src="require('../assets/img/flag-'+[card.original_language]+'.png')" 
          :alt="'flag-'+card.original_language"
          class="img-fluid"   
        >
      </li>
      <li>
        <span>Vote Average: </span>
        <!-- richiamo la funzione che arrotonda vote.average e lo trasforma in un numero da 1 a 5 -->
        <h4>{{getCeil(card.vote_average)}} </h4>
        <i class="fas fa-star"></i>
      </li>
    </ul>
</template>

<script>
export default {
  name: "Card",
  props: { // props mette in comunicazione Card con il genitore Main
    card: Object, // card viene passato dal genitore
  },
  methods: {
    getCeil(num){
      let n = Math.ceil(num)/2
      return Math.ceil(n)
    }
  },
};
</script>

<style lang="scss" scoped>
// importo le variabili 
@import "../assets/style/vars.scss";
  ul {
    background-color: $color-header;
    list-style: none;
    cursor: pointer;
    transition: all 0.8s;
    padding: 30px;
    min-height: 350px;
    &:hover {
      filter: brightness(1.4);
      transform: scale(1.1);
    }
    li {
      span {
        color: $color-btn;
        font-size: 0.8em;
        text-transform: uppercase;
      }
      h2,
      h3,
      h4 {
        font-size: 1.2em;
      }
      img {
        height: 1.5rem;
        padding-bottom: 7px;
        margin-left: 7px;
      }
    }
}
</style>