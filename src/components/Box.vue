<template>
  <div class="box has-text-wweight-bold">
    <slot/>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
export default defineComponent( {
  name: "BoxComponent"
})
</script>

<style scoped>
.box{
  background: #FAF0CA;
}
</style>