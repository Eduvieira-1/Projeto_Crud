<template>
   <nav>
        <ul class="header">
          <li class="header-top" v-for="(rota,index) in rotas" :key="index">
           <router-link  
            class="home" 
           :to="rota.path ? rota.path : '/' ">{{ rota.titulo }}
           </router-link>
           </li>
        
        </ul>
      </nav>
</template>

<script>


export default {


     props: {
       rotas: {
         type: Array,
         required: true
      }
    }
  }
</script>

<style>

</style>