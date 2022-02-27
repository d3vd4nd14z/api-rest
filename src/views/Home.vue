<template>
  <div class="home">
    <Titulo title="Este es el titulo de mi componente Home"/>
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>

import Titulo from '../components/Titulo.vue'

export default {
  name: 'Home',
  components: {
    Titulo
  }
}
</script>
