<template>
    <div class="box">
        <div class="column">
            <div class="column is-8" role="form" arial-label="formulario para criacao de uma nova tarefa">
                <input type="text" class="input" v-model="descricao" placeholder="Qual tarefa você deseja iniciar?">
            </div>
            <div class="column">
               <Cronometro/> 
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
import Cronometro from './Cronometro.vue';

export default defineComponent({
    name: 'FormularioVue',
    components:{
        Cronometro,
    },
    emits: ['aoTemporizadorFinalizado'],
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
            console.log("tempoAposFinalizar: " + this.tempoEmSegundos);
            console.log("FINALIZANDO")
            this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
            console.log("TempoDecorrido: " + this.tempoEmSegundos)
            console.log("Descricao: " + this.descricao)
            this.descricao = '';
            this.tempoEmSegundos = 0;
        }
    }
})


</script>