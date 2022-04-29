<template>
  <button class="button" @click="clicado()" :disabled="disabled">
    <span class="icon">
      <i :class="iconPrefix"></i>
    </span>
    <span> {{label}} </span>
  </button>
</template>
<script lang="ts">
import {defineComponent} from "vue";

export default defineComponent({
    emits:['clicado'],
    props: {
        disabled: {
            type: Boolean,
            default: false
        },
        iconPrefix: {
            type: String,
            default: 'fas info'
        },
        label: {
            type: String,
            default: 'Label'
        }
    },
    methods:{
        clicado(): void {
            this.$emit('clicado', 'Botão clicado!');
        }
    }
})
</script>