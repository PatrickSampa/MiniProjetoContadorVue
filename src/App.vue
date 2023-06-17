<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter">
      <FormularioVue/>
      <div class="lista">
        <TaretaProjeto/>
      </div>
    </div>
  </main>
</template>

<script>
import BarraLateral from './components/BarraLateral.vue';
import FormularioVue from './components/FormularioVue.vue'
import TaretaProjeto from "./components/TarefaProjeto.vue"

export default {
  name: 'App',
  components: {
    BarraLateral,
    FormularioVue,
    TaretaProjeto
}
}
</script>

<style>


</style>
