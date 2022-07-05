<template>
  <button class="button" @click="clicando" :disabled="desabilitando">
    <span class="icon">
      <i :class="icone"></i>
    </span>
    <span>{{ texto }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent( {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Button",
  emtis: ['clicando'],
  props: {
    desabilitando:{
      type: Boolean
    },
    icone:{
      type:String,
      required:true
    },
    texto:{
      type:String,
      required: true
    }
  },
  methods:{
    clicando(){
      this.$emit("clicando")
    }
  }
})
</script>

<style scoped>

</style>