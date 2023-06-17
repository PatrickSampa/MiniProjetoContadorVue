<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter">
      <FormularioVue @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TaretaProjeto v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa"/>
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
  },
  methods:{
    salvarTarefa(tarefas){
      this.tarefas.push(tarefas)
      console.log("Tarefas? " + JSON.stringify(tarefas))
    }
  },
  data () {
    return {
      tarefas: []
    }
  }
}
</script>

<style>
.lista{
  padding: 1.25rem;
}


</style>
