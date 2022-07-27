<template>
  <main class="columns is-gapless is-multiline modo-escuro" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <FormularioTracker @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa v-for="(tarefa,index) in tarefas" :key="index" :tarefa="tarefa"/>
        <BoxComponent v-if="listIsEmpty">
          Você não possui tarefas :(
        </BoxComponent>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import TarefaInterface from "@/Interface/TarefaInterface";
import BarraLateral from "@/components/BarraLateral.vue";
import FormularioTracker from "@/components/Formulario.vue";
import BoxComponent from "@/components/Box.vue";
import Tarefa from "@/components/Tarefa.vue";

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioTracker,
    Tarefa,
    BoxComponent
  },
  data () {
    return {
      tarefas: [] as TarefaInterface[],
      modoEscuroAtivo: false
    }
  },
  computed:{
    listIsEmpty(): boolean{
      return this.tarefas.length === 0;
    }
  },
  methods:{
    salvarTarefa (tarefa: TarefaInterface) {
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivo: boolean){
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }

});
</script>

<style>
.lista{
  padding: 1.25rem;
}
main{
  --bg-primario: #ffff;
  --text-primario: #000;
}
main.modo-escuro{
  --bg-primario: #2b2d42;
  --text-primario: #ddd;
}
.conteudo{
  background-color: var(--bg-primario);
}
</style>
