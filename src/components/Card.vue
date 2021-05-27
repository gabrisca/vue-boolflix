<template>
  <div>
    <ul>
      <li>
        <span>Title: </span>
        <h2>{{ card.title || card.name }}</h2>
      </li>
      <li>
        <span>Original Title: </span>
        <h3>{{ card.original_title || card.original_name }}</h3>
      </li>
      <li>
        <span>Original Language: </span>
        <h4>{{ card.original_language }}</h4>
      </li>
      <li>
        <span>Vote Average: </span>
        <h4>{{ card.vote_average }}</h4>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    card: Object,
  },
};
</script>

<style lang="scss" scoped>
/* // importo le variabili */
@import "../assets/style/vars.scss";
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
</style>