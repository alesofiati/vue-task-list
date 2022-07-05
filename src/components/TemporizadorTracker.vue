<template>
    <CronometroTracker :tempo-em-segundos="tempoEmSegundos"/>

    <Button @clicando="iniciar" icone="fas fa-play" texto="play" :desabilitando="cronometroRodando"></Button>
    <Button @clicando="finalizar" icone="fas fa-stop" texto="stop" :desabilitando="!cronometroRodando"></Button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import CronometroTracker from "@/components/Cronometro.vue";
import Button from "@/components/Button.vue";
export default defineComponent( {
  name: "TemporizadorTracker",
  emits: ['aoTemporizadorFinalizado'],
  components:{
    Button,
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
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos);
      this.tempoEmSegundos = 0;
    }
  }
})
</script>

<style scoped>

</style>