<template>
    <CronometroTracker :tempo-em-segundos="tempoEmSegundos"/>

    <button class="button" @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
    </button>

    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
    </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTracker from "@/components/Cronometro.vue";
export default defineComponent( {
  name: "TemporizadorTracker",
  components:{
    CronometroTracker
  },

  data (){
    return {
      tempoEmSegundos:0,
      cronometro:0,
      cronometroRodando: false,
    }
  },

  methods: {
    iniciar () {
      this.cronometroRodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1
      },1000)

    },
    finalizar () {
      this.cronometroRodando = false;
      clearInterval(this.cronometro)
    }
  }
})
</script>

<style scoped>

</style>