<script setup>
import {ref} from 'vue'

const dynamicId = ref('light')

const toggleDarkmode = ()=>{
  if(dynamicId.value === 'light'){
    dynamicId.value = 'dark'
  }else{
    dynamicId.value = 'light'
  }
}

const code = {
  dark:"<div id=\"dark\">今日はいい天気だ。</div>",
  light:"<div id=\"light\">今日はいい天気だ。</div>"
}
</script>
<template>
  <div class="slidev-layout default">
    <div class="container">
      <div v-bind:id="dynamicId">今日はいい天気だ。</div>
      <button @click="toggleDarkmode">toggleDarkmode()</button>

      <div class="code">
        描画:
        <code>
        {{ "<div id=\"" + dynamicId + "\">今日はいい天気だ。</div>" }}
        </code>
      </div>
    </div>
  </div>
</template>
<style scoped>
.container{
  padding: 2em;
  background: #fafafa;
}
.code{
  margin: 1em 0 0;
}
#dark{
  margin: 0 0 1em;
  padding: 1em;
  background-color: #000;
  color: #fff;
}
#light{
  margin: 0 0 1em;
  padding: 1em;
  background-color: #fff;
  color: #333;
}
button{
  background-color: #99ee02;
  padding: 0.2em 1em;
  border-radius: 0.5em;
}
</style>