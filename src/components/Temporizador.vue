<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmSegundos="tempoEmSegundos" />
    <Button @clicado="iniciar" :disabled="runtime" :iconPrefix="'fas fa-play'" :label="'paly'"/>
    <Button @clicado="finalizar" :disabled="!runtime" :iconPrefix="'fas fa-stop'" :label="'stop'"/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Cronometro from "./Cronometro.vue";
import Button from "./Button.vue";
export default defineComponent({
  emits: ['aoTemporizadorFinalizado'],
  name: "Temporizador",
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      runtime: false,
    };
  },
  methods: {
    iniciar(event: string) {
      console.log("Iniciando");
      console.log(event);
      if (!this.runtime) {
        this.cronometro = setInterval(() => {
          console.log("Incrementando o contador");
          this.tempoEmSegundos++;
        }, 1000);

        this.runtime = true;
      }
    },
    finalizar(event: string) {
      console.log(event);
      clearInterval(this.cronometro);
      this.runtime = false;
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
      this.tempoEmSegundos = 0;
      console.log("finalizando");
    },
  },
  components: { Cronometro, Button },
});
</script>