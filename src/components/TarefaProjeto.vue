<template>
<div class="box has-text-weight-bold">


    <div class="columns">
        <div class="column is-7">
            Descricao da tarefa
        </div>
        <div class="column">
            {{tempoDecorrido}}
        </div>
    </div>
</div>


</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'tarefaProjeto',
    props:{
        tempoEmSegundos: {
            type: Number,
            default: 0,
        }
    },
    computed:{
        tempoDecorrido(){
            return new Date(this.tempoEmSegundos).toISOString().substr(11,8)
        }
    }
})



</script>