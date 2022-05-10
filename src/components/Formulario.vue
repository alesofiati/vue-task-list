<template>
  <div class="box">
    <div class="columns">
      <div class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
        <input type="text" class="input" placeholder="Qual rafere você deseja inicias?">
      </div>
      <div class="column">
        <div class="is-flex is-align-items-center is-justify-content-space-between">

          <TemporizadorTracker/>

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
  components: {TemporizadorTracker},
})
</script>

<style scoped>

</style>