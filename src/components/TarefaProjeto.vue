<template>
<div class="box has-text-weight-bold">


    <div class="columns">
        <div class="column is-7">
            {{tarefa.descricao}}
        </div>
        <div class="column">
            <CronometroVue :tempoEmSegundos="tarefa.duracaoEmSegundos"/> 
        </div>
    </div>
</div>


</template>

<script>
/* eslint-disable */
import { defineComponent } from 'vue';
import CronometroVue from './CronometroVue.vue';
import('vue').PropType

export default defineComponent({
    name: 'tarefaProjeto',
    components:{
        CronometroVue,
    },
    props:{
        tarefa:{
            type: Object,
            required:true
        }
    }
})



</script>


<style scoped>
.box{
    background: #FAF0CA;
}

</style>