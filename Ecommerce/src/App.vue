<script>
  import Header from './components/Header.vue'
  import ImageProduct from './components/ImageProduct.vue'
  import DetailsProduct from './components/DetailsProduct.vue'

  export default{
    components: {
      Header,ImageProduct,DetailsProduct
    }
  }
</script>

<template>
  <Header/>
  <article class="container">
    <ImageProduct/>
    <DetailsProduct/>
  </article>
</template>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Kumbh+Sans:wght@400;700&display=swap');
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'kumbh sans', sans-serif;
  }
  .container{
    width: 100%;
    max-width: 1200px;
    margin: auto;
  }
  article{
    display: flex;
  }

  @media screen and (max-width: 768px){
    article{
      flex-direction: column;
      align-items: center;
    }
  }
</style>
