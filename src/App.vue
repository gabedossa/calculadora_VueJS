<template>
  <Calculadora />
</template>

<script>
import Calculadora from './components/Calculadora.vue'

export default {
  components: { Calculadora },
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background: #11111b;
  min-height: 100vh;
}
</style>
