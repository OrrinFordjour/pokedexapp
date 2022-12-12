<template>
  <PokeNav/>
  <PokeGrid/>
</template>

<script>
import PokeGrid from './components/PokeGrid.vue'
import PokeNav from './components/PokeNav.vue';

export default {
  name: 'App',
  components: {
    PokeGrid,
    PokeNav
}
}
</script>

<style>

</style>
