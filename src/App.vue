<template>
  <div class="corpo">
      
      <meu-menu :rotas="routes"></meu-menu>

    <transition name="pagina">
      <router-view></router-view>
    </transition>

  </div>
</template>

<script>

import { routes } from './routes';
import Menu from './componentes/shared/menu/Menu.vue';


export default {

  components: {
    'meu-menu': Menu
  },

  data(){

    return{

      routes
    }
  }
};

</script>

<style>
.corpo {
  font-family: Helvetica, sans-serif;
  width: 96%;
  margin: 0 auto;
}


.header{
  list-style: none;
}


.header-top {
  display: inline-block;
    padding: 10px 15px !important;
    border: 1px solid #0093E5;
    border-radius: 10px; 
    margin-left: 10px;
}

.header-top a{
  text-decoration: none;
  color: #0093E5;
}

.header-top:hover, .header-top a:hover{
    -webkit-transition: all 0.3s;
    -o-transition: all 0.3s;
    transition: all 0.3s;
    background: #0093E5;
    color: white;
}

  .pagina-enter, .pagina-leave-active{
     opacity: 0;
  }

  .pagina-enter-active, .pagina-leave-active{
      transition: opacity .4s;
  }

</style>

