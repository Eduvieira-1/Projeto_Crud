<template>

  <div class="painel">
    <h2 class="painel-titulo" @dblclick="visivel = !visivel">{{ titulo }}</h2>

   <transition name="painel-fade">
      <div class="painel-conteudo"  v-show="visivel">
          <slot></slot>
      </div>
  </transition>
    
  </div>
   
</template>

<script>
export default {

  props: ['titulo'],

  data(){

   return{
     visivel: true
   }

  }

}
</script>

<style scoped>

  .corpo{
    font-family: Helvetica, sans-serif;
    width: 96%;
    margin: 0 auto;
  }

  .centralizado{
    text-align: center;
  }

  .painel-titulo{
    cursor: pointer;
    color:white;
    font-size: 16px;
  }

  .lista-fotos{
    list-style: none;
    
  }

  .lista-fotos .lista-fotos-item{
    display: inline-block;
  }

  .imagem-responsiva{
    width: 100%;
  }

    /* estilo do painel */ 

   .painel {
    display: inline-block;
    margin: 5px;
    box-shadow: 5px 5px 10px #0093e5;
    width: 200px;
    vertical-align: top;
    text-align: center;
  }

  .painel .painel-titulo {
    text-align: center;
    background: #0093e5;
    margin: 0;
    padding: 10px;
    text-transform: uppercase;
  }

  .painel *{
    margin: 16px;
    padding: 0;
    box-shadow: 5px 5px 10px grey;
  }


  .paniel-fade-enter, .painel-fade-leave-active{
     opacity: 0;
  }

  .paniel-fade-enter-active, .painel-fade-leave-active{
      transition: opacity .4s;
  }

</style>
