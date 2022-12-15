<template>
    <BoxView>
        <div class="columns">
            <div class="column is-7">
            {{tarefa.descricao || 'Tarefa sem descrição'}}
            </div>
            <div class="column" >
                <CronometroTarefa :tempoEmSegundos="tarefa.duracaoEmSegundos" />
            </div>
        </div>
    </BoxView>
</template>
<script lang="ts">
import { defineComponent, PropType } from "vue";
import ITarefa from "@/Interfaces/ITarefa";
import BoxView from './Box.vue'
import CronometroTarefa from "./Cronometro.vue";
export default defineComponent({ 
    name: 'TarefaRealizada',
    components:{
        CronometroTarefa,
        BoxView
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
});
</script>
