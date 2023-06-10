<template>
    <div class="box">
        <div class="column">
            <div class="column is-8" role="form" arial-label="formulario para criacao de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?">
            </div>
            <div class="column">
                <section>
                    <strong>{{ tempoDecorrido }}</strong>
                </section>
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

export default defineComponent({
    name: 'FormularioVue',
    //ESTADO INICIAL
    data(){
        return {
            tempoEmSegundos: 0,
            cronometro: 0,
            cronometroRodando: false,  
        }
    },
    computed: {
        tempoDecorrido(){
            return new Date(this.tempoEmSegundos * 1000 ).toISOString().substr(11,8)
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
        }
    }
})


</script>