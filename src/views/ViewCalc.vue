<template>
  <div>
    <h1>Calculadora de IMC</h1>
    <slot></slot>
  </div>
</template>
<script>
import { defineComponent } from "vue";

export default defineComponent({});
</script>
<style scoped>
div {
  display: flex;
  flex-direction: column;
  padding-top: 5vh;
}
</style>
