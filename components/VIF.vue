<script setup>
import {ref} from 'vue'
const input = ref(null)
</script>
<template>
  <div class="slidev-layout default">
    <div class="container">
      <input v-model="input">
      <p v-if="input === null">nullです</p>
      <p v-else-if="/^[0-9]+$/.test(input)">数字です</p>
      <p v-else-if="/^[A-Za-z]+$/.test(input)">英字です</p>
      <p v-else>それ以外です</p>
    </div>
  </div>
</template>
<style scoped>
.container{
  padding: 2em;
  background: #fafafa;
}
input{
  padding: 0.5em;
  border-radius: 6px;
  border: 1px solid #eee;
}
</style>