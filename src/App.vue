<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter">
      <FormularioVue/>
    </div>
  </main>
</template>

<script>
import BarraLateral from './components/BarraLateral.vue';
import FormularioVue from './components/FormularioVue.vue'

export default {
  name: 'App',
  components: {
    BarraLateral,
    FormularioVue
}
}
</script>

<style>


</style>
