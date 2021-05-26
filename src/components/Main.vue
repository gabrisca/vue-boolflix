<template>
  <div class="container mt-3 mb-3">
    <ul>
      <li>
        <span>Title: </span>
        <h2>{{ movie.title }}</h2>
      </li>
      <li>
        <span>Original Title: </span>
        <h3>{{ movie.original_title }}</h3>
      </li>
      <li>
        <span>Original Language: </span>
        <h4>{{ movie.original_language }}</h4>
      </li>
      <li>
        <span>Vote Average: </span>
        <h4>{{ movie.vote_average }}</h4>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Main",
  // con props permetto la comunicazione tra genitore (App) e figlio (Main)
  props: {
    movie: Object,
  },
};
</script>

<style lang='scss' scoped>
/* // importo le variabili */
@import "../assets/style/vars.scss";
.container {
  ul {
    background-color: $color-header;
    list-style: none;
    cursor: pointer;
    transition: all 0.8s;
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
    }
  }
}
</style>