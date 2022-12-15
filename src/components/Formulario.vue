<template>
    <div class="box formulario">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
                <input type="text" class="input" placeholder="Qual tarefa voce deseja iniciar" v-model="descricao"/>
            </div>
            <div class="column">
                <TemporizadorTarefa @temporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>
    
<script lang="ts">
import { defineComponent } from 'vue';
import  TemporizadorTarefa  from './Temporizador.vue';
export default defineComponent({
    name: 'FormularioPrincipal',
    emits: ['aoSalvarTarefa'],
    components: {
        TemporizadorTarefa
    },
    data() {
        return {
            descricao: ''
        }
    },
    methods: {
        finalizarTarefa(tempoDecorrido: number) : void{ 
            this.$emit('aoSalvarTarefa',{
                duracaoEmSegundos: tempoDecorrido,
                descricao: this.descricao
            })
            this.descricao = '';  
        }
    },
})
</script>
<style>
.formulario{
    color: var(--texto-primario);
    background-color:  var(--bg-primario);
}
</style>
