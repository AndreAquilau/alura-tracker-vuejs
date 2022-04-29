<template>
  <main class="columns is-gapless is-multiline" :class="tema">
    <div class="column is-one-quarter">
      <BarraLateral @alterar-tema="altereModo"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @tarefa="setTarefa" />
      <div class="lista">
        <Tarefa
          v-for="(tarefa, index) in tarefas"
          :key="index"
          :tarefa="tarefa"
        />
      </div>
      <Box v-if="listaEstaVazia">
        <span>Você não está muito produtivo hoje :( </span>
      </Box>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import BarraLateral from "./components/BarraLateral.vue";
import Formulario from "./components/Formulario.vue";
import Tarefa from "./components/Tarefa.vue";
import { ITarefa } from "./interface/tarefa.interface";
import Box from "./components/Box.vue";

export default defineComponent({
  name: "App",
  setup() {
    const tarefas = ref<ITarefa[]>([]);
    return {
      tarefas,
    };
  },
  data() {
    return {
      modoEscuro: false, 
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return (this.tarefas.length === 0);
    }, 
    tema(): string {
      if(this.modoEscuro) {
        return 'modo-escuro'
      } else {
        return ''
      }
    },
  },
  methods: {
    setTarefa(tarefa: ITarefa): void {
      console.log(tarefa);
      this.tarefas.push(tarefa);
    },
    altereModo(escuro: boolean) {
      this.modoEscuro = escuro;
    },
  },
  components: {
    BarraLateral,
    Formulario,
    Tarefa,
    Box,
  },
});
</script>

<style scoped>
.lista {
  padding: 1.25rem;
}

main {
  --bg-primario: #FFFFFF;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2B2D42;
  --texto-primario: #DDDDDD;
}

.conteudo{
  background-color: var(--bg-primario);
}
</style>
