<template>
  <div class="box formulario">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual rafere você deseja inicias?" v-model="descricao">
      </div>
      <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">

          <TemporizadorTracker @aoTemporizadorFinalizado="finalizarTarefa"/>

        </div>

      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import TemporizadorTracker from "@/components/TemporizadorTracker.vue";
export default defineComponent({
  name: "FormularioTracker",
  emits: ['aoSalvarTarefa'],
  components: {TemporizadorTracker},
  data (){
    return {
      descricao: ''
    }
  },
  methods:{
    finalizarTarefa(tempoDecorrido: number):void{
      this.$emit('aoSalvarTarefa', {
        duracaoEmSegundos: tempoDecorrido,
        descricao: this.descricao
      })
      this.descricao = ''
    }
  }
})
</script>

<style>
.formulario{
  color: var(--text-primario);
  background-color: var(--bg-primario);
}
</style>