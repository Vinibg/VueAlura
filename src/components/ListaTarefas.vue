<template>
    <BoxList>
        <div class="columns">
            <div class="column is-7">
                {{tarefa.descricao}}
            </div>
            <div class="column">
                <CronometroVue :tempoEmSegundos='tarefa.duracaoEmSegundos'/>     
            </div>
        </div>
    </BoxList>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import CronometroVue from "./Cronometro.vue";
import BoxList from "./BoxList.vue";
import ITarefa from "../interfaces/ITarefa";

export default defineComponent({
    name:'ListaTarefas',
    components: {
        CronometroVue,
        BoxList
    },
    props:{
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>

