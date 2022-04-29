<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="">
    </h1>
    <button class="button" @click="alterarTema()">
      {{textoBatao}}
    </button>
  </header>
</template>

<script lang="ts">
  import {defineComponent} from 'vue';
  
  export default defineComponent({
    name: 'BarraLateral',
    emits:['alterarTema'],
    data(){
      return {
        modoEscuroAtivo: false
      }
    },
    computed: {
      textoBatao(): string {
        if(this.modoEscuroAtivo){
          return 'Ativar Modo Claro';
        } else {
          return 'Ativar Modo Escuro'
        }
      }
    },
    methods:{
      alterarTema():void {
        this.modoEscuroAtivo = !this.modoEscuroAtivo;
        this.$emit('alterarTema', this.modoEscuroAtivo);
      }
    }
  });
  
</script>

<style scoped>
/*todo o estilo do comeponente*/
header {
  padding: 1rem;
  background: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}
@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>
