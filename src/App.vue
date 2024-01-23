<template>
  <CarMod />
</template>

<script>
import CarMod from './components/CarMod.vue'

export default {
  name: 'App',
  components: {
    CarMod
  }
}
</script>

<style>

*,
*::after,
*::before {
    margin: 0;
    padding: 0;
    -webkit-box-sizing: inherit;
    box-sizing: inherit;
}
</style>
