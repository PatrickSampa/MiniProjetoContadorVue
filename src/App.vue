<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuroAtivo}">
    <div class="column is-one-quarter">
      <BarraLateral @aotemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioVue @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TaretaProjeto v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa"/>
        <div class="box has-text-weight-bold" v-if="listaVazia">        
          você não esta produtivo hoje
        </div>
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
    },
    trocarTema(modoEscuroAtivo){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  },
  computed:{
    listaVazia(){
      return this.tarefas.length===0
    }
  },
  data () {
    return {
      tarefas: [],
      modoEscuroAtivo: false
    }
  }
}
</script>

<style>
.lista{
  padding: 1.25rem;
}

main {
  --bg--primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro{
  --bg--primario: #2b2d42;
  --texto-primario: #ddd;
}

.conteudo{
  background-color: var(--bg--primario);
}


</style>
