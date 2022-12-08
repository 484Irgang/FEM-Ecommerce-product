<script>
  import Header from './components/Header.vue'

  export default{
    components: {
      Header
    }
  }
</script>

<template>
  <Header/>
</template>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  .container{
    width: 100%;
    max-width: 1200px;
    padding: 0 2%;
    margin: auto;
  }
</style>
