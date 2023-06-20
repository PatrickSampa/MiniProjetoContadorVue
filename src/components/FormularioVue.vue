<template>
    <div class="box formulario">
        <div class="column">
            <div class="column is-8" role="form" arial-label="formulario para criacao de uma nova tarefa">
                <input type="text" class="input" v-model="descricao" placeholder="Qual tarefa você deseja iniciar?">
            </div>
            <div class="column">
               <CronometroVue :tempoEmSegundos="tempoEmSegundos"/> 
                <button class="button" @click="iniciar" :disabled="cronometroRodando">
                    <span class="icon">
                        <i class="fas fa-play"></i>
                    </span>
                    <span>play</span>
                </button>
                <button class="button" @click="finalizar" :disabled='!cronometroRodando'>
                    <span class="icon">
                        <i class="fas fa-stop"></i>
                    </span>
                    <span>stop</span>
                </button>
            </div>
        </div>
    </div>
</template>

<script>
import { defineComponent } from 'vue';
import CronometroVue from './CronometroVue.vue';

export default defineComponent({
    name: 'FormularioVue',
    components:{
        CronometroVue,
    },
    emits: ['aoSalvarTarefa'],
    //ESTADO INICIAL
    data(){
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false,  
            descricao : "",
        }
    },
    methods: {
        iniciar(){
            this.cronometroRodando = true;
            this.cronometro = setInterval(() =>{
                this.tempoEmSegundos +=1
                console.log("cronometro: " + this.cronometro)
            },1000)
            console.log("INICIOU")
        },
        finalizar(){
            this.cronometroRodando = false;
            clearInterval(this.cronometro)
            this.$emit('aoSalvarTarefa', {
                duracaoEmSegundos: this.tempoEmSegundos,
                descricao: this.descricao
            })
            this.descricao = '';
            this.tempoEmSegundos = 0;
        }
    }
})


</script>


<style>

.formulario{
    color: var(--texto-primario);
    background-color: var(--bg--primario);
}

</style>