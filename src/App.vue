<template>
  <main class="columns is-gapless is-multiline" :class="{'modo-escuro': modoEscuroAtivo}">
    <div class="column is-one-quarter ">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioPrincipal @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <TarefaRealizada v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/> 
        <BoxView v-if="listaEstaVazia">
          Voce não realizou nenhuma tarefa ainda hoje 
        </BoxView>
      </div>
      
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioPrincipal from './components/Formulario.vue';
import TarefaRealizada from './components/Tarefa.vue';
import ITarefa from './Interfaces/ITarefa';
import BoxView from './components/Box.vue';
export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioPrincipal,
    TarefaRealizada,
    BoxView
  },
  data(){
    return{
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }

  },
  computed:{
    listaEstaVazia() : boolean{
      return this.tarefas.length === 0;
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa){
      this.tarefas.push(tarefa) 
    },
    trocarTema(modoEscuroAtivo : boolean){
      this.modoEscuroAtivo = modoEscuroAtivo;
    }
  },
});
</script>

<style>
.lista{
    padding: 1.25rem;
}

main{
  --bg-primario: '#fff';
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo{
  background-color: var(--bg-primario);
}
</style>
