<template>
  <BoxComponent>
    <div class="columns">
      <div class="column is-7">
        {{ tarefa.descricao || 'Tarefa sem descrição' }}
      </div>
      <div class="column">
        <Cronometro :tempoEmSegundos="tarefa.duracaoEmSegundos"/>
      </div>
    </div>
  </BoxComponent>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Cronometro from "@/components/Cronometro.vue";
import BoxComponent from "@/components/Box.vue";
import TarefaInterface from "@/Interface/TarefaInterface";
export default defineComponent( {
  /* eslint-disable */
  name: "Tarefa",
  components: {
    Cronometro,
    BoxComponent
  },
  props:{
    tarefa: {
      type: Object as PropType<TarefaInterface>,
      required: true
    }

  }
})
</script>