<template>
  <main>
    <div class="columns is-gapless is-multiline">
        <div class="column is-one-quarter">
          <BarraLateral />
        </div>
        <div class="column is-three-quarter">
          <FormularioTarefa @aoSalvarTarefa="salvarTarefas"/>
          <div class="lista">
            <ListaTarefas v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/>
            <BoxList v-if="listaVazia">
              Você ainda não realizou nenhuma tarefa.
            </BoxList>
          </div>
        </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import FormularioTarefa from './components/Formulario.vue';
import ListaTarefas from './components/ListaTarefas.vue';
import BoxList from './components/BoxList.vue';
import ITarefa from './interfaces/ITarefa'

export default defineComponent({
    name: "App",
    components: { BarraLateral, FormularioTarefa, ListaTarefas, BoxList },
    data(){
      return {
        tarefas: [] as ITarefa[]
      }
    },
    computed: {
      listaVazia ():  boolean {
        return this.tarefas.length === 0
      }
    },
    methods: {
      salvarTarefas(tarefa: ITarefa){
        this.tarefas.push(tarefa)
      }
    }
});
</script>

<style>
.lista{
  padding: 1.25rem;
}
</style>
