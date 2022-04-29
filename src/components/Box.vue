<template>
  <div class="box has-text-weight-bold">
      <slot></slot>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "@vue/runtime-core";

export default defineComponent({
    name: 'Box'
})
</script>

<style scoped>
.box {
  background: #faf0ca;
}
</style>