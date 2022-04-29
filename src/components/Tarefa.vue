<template>
  <Box>
    <div class="columns">
      <div class="column is-7 descricao">{{tarefa.descricao || 'Tarefa sem descrição'}}</div>
      <div class="column tempo">
        <Cronometro :tempoEmSegundos="tarefa.tempoEmSegundos" />
      </div>
    </div>
  </Box>
</template>

<script lang="ts">
import { ITarefa } from "@/interface/tarefa.interface";
import { defineComponent, PropType } from "@vue/runtime-core";
import Cronometro from "./Cronometro.vue";
import Box from "./Box.vue";

export default defineComponent({
  name: "Tafera",
  components: { Cronometro, Box },
  props: {
    tarefa: {
        type: Object as PropType<ITarefa>,
        required: true,
    }
  },
});
</script>