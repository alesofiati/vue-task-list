<template>
  <main class="columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter">
      <FormularioTracker @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa"/>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TarefaInterface from "@/Interface/TarefaInterface";
import BarraLateral from "@/components/BarraLateral.vue";
import FormularioTracker from "@/components/Formulario.vue";
import Tarefa from "@/components/Tarefa.vue";

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTracker,
    Tarefa
  },
  data () {
    return {
      tarefas: [] as TarefaInterface[]
    }
  },
  methods:{
    salvarTarefa (tarefa: TarefaInterface) {
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
