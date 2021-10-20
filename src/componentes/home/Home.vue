<template>
  <div>
    <h1 class="centralizado">{{ titulo }}</h1>

    <input
      type="search"
      class="filtro"
      @input="filtro = $event.target.value"
      placeholder="filtre por parte do titulo"
    />

    <ul class="lista-fotos">
      <li 
        class="lista-fotos-item" 
        v-for="(foto, index) in fotosComFiltro" 
        :key="index"
      >

        <meu-painel :titulo="foto.titulo">
 
          <imagem-responsiva v-meu-transform :url="foto.url" :titulo="foto.titulo"/>
          <meu-botao 
            tipo="button" 
            rotulo="Remover" 
            @botaoAtivado="remove(foto)"
            :confirmacao="true"
            estilo="padrao"
          />
          
          <!-- @click.native="remove(foto)" -->
            
        </meu-painel>

      </li>
    </ul>
  </div>
</template>

<script>
import Painel from "../shared/painel/Painel.vue";
import ImagemResponsiva from "../shared/imagem-responsiva/ImagemResponsiva.vue";
import Botao from '../shared/botao/Botao.vue';

export default {
  components: {
    'meu-painel': Painel,
    'imagem-responsiva': ImagemResponsiva,
    'meu-botao': Botao
  },

  data() {
    return {
      titulo: "Vue",
      fotos: [],
      filtro: "",
    };
  },

  computed: {
    fotosComFiltro() {
      if (this.filtro) {
        let exp = new RegExp(this.filtro.trim(), "i");
        return this.fotos.filter((foto) => exp.test(foto.titulo));
      } else {
        return this.fotos;
      }
    },
  },


  methods: {

    remove(foto){
        alert('Remove a foto! ' + foto.titulo);
    }

  },

  created() {
    this.$http
      .get("http://localhost:3000/v1/fotos")
      .then((res) => res.json())
      .then((fotos) => (this.fotos = fotos));

    // promise.then(res => {
    //   res.json().then(fotos => this.fotos = fotos)
    // });
  },
};
</script>

<style>


.centralizado {
  text-align: center;
    cursor: pointer;
    -webkit-transition: all 0.4s;
    -o-transition: all 0.4s;
    transition: all 0.4s;
    color: transparent;
    background: black;
    -webkit-background-clip: text;
    -moz-background-clip: text;
    background-clip: text;
    text-shadow: 0px 3px 3px rgba(255,255,255,0.5);
}

.painel-titulo {
  color: white;
  font-size: 16px;
}

.lista-fotos {
  list-style: none;
}

.lista-fotos .lista-fotos-item {
  display: inline-block;
}

.filtro {
  display: block;
  margin-left: 45px;
  width: 81%;
  outline: none;
  padding: 10px 5px 10px 5px;
  border: 1px solid #0093e5;
  border-radius: 10px;
}
</style>

