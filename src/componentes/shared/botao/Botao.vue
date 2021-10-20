<template>
   <button @click="disparaAcao()" class="botao" :class="estiloDoBotao" :type="tipo">{{ rotulo }}</button>
</template>

<script>

export default {

  props: {
      tipo:{
          required:  true,
          type: String
      },

      rotulo:{
          required: true,
          type: String
      },

      confirmacao: Boolean,
      estilo: String
  } ,

  methods:{
      disparaAcao(){

          if(this.confirmacao){
            if(confirm('Confirma operação?')){
            this.$emit('botaoAtivado');
             }
             return;
           }
            this.$emit('botaoAtivado');  
        }
    },


  computed:{
     estiloDoBotao(){
         if(this.estilo == 'padrao' || !this.estilo) return 'botao-padrao';
         if(this.estilo == 'perigo') return 'botao-perigo';
     }
  }
}
</script>

<style scoped>
 .botao {
        display: inline-block;
        padding: 5px 5px;
        border-radius: 3px;
        margin: 10px;
        font-size: 1.2em;
    }

    .botao-perigo {
        cursor: pointer;
        background: white;
        border: 1px solid firebrick;
        color: firebrick;
    }

    .botao-perigo:hover {
        transition: all 0.4s;
        background-color: firebrick;
        color: white;
    }

    

    .botao-padrao {
        cursor: pointer;
        background: white;
        border: 1px solid darkcyan;
        color: darkcyan;
    }

    .botao-padrao:hover {
        transition: all 0.4s;
        background-color: darkcyan;
        color: white;
    }


</style>