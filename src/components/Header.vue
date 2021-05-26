<template>
  <header class="d-flex justify-content-between align-items-center ps-5 pe-5">
    <div>logo</div>
    <div>
      <form class="d-flex mt-3 mb-3">
    <div>
     <input class="form-control" type="text" placeholder="Find your movie"> 
    </div>
    <div class="ms-3">
      <button class="btn btn-primary mc_btn"> 
        Search
      </button>
    </div>
  </form>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style lang='scss' scoped>
/* // importo le variabili */
@import '../assets/style/vars.scss';
  header{
    background: $color-header;
    height: 65px;
    .mc_btn {
      background-color: $color-btn;
      border-color: transparent;
      &:hover{
        filter: brightness(1.2);
      }
    }
  }
</style>