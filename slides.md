---
theme: Default
class: text-center
highlighter: shiki
lineNumbers: false
info: |
  ## Vue.js道場

drawings:
  persist: false
transition: slide-left
css: unocss
title: Vue.js
---

# <logos-vue />
# Vue.js

2023 - 2024

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    次へ <carbon:arrow-right class="inline"/>
  </span>
</div>



---
transition: fade-out
level: 2
---

# コンテンツ

<Toc columns="2"></Toc>

---
level: 2
layout: two-cols
---

# Vol.00 JS基礎

---
src: ./pages/aboutjs.md
---

---
src: ./pages/var.md
---

---
src: ./pages/operator.md
---

---
src: ./pages/comparison.md
---

---
src: ./pages/conditional.md
---

---
src: ./pages/for.md
---

---
src: ./pages/function.md
---
---
src: ./pages/class.md
---
---
src: ./pages/anti-intentional.md
---

---
level: 2
layout: two-cols
---
# Vol.01 はじめてのVue.js

---
src: ./pages/materials.md
---

---
src: ./pages/aboutvue.md
---

---
src: ./pages/vuecdn.md
---



---
level: 2
---
# Vol.02 SFCにふれる
.vueファイル

Vue.jsでは.vueという拡張子の単一ファイルコンポーネント（SFC）を使うことができる。
SFCにはscript、template、styleというタグが含まれており、それぞれ処理・構造・スタイルを扱う。SFCはそのままではブラウザは解読できないため、ビルドが必要となる。

```vue
<script setup>
  import { ref } from 'vue'
  const greeting = ref('Hello World!') 
</script>

<template>
  <p class="greeting">{{ greeting }}</p>
</template>

<style>
  .greeting { color: red; font-weight: bold; }
</style>
```
---
src: ./pages/nodejs.md
---

---
src: ./pages/createvue.md
---

---
src: ./pages/SPA.md
---

---
src: ./pages/component.md
---

---
src: ./pages/lifecycle.md
---

---
src: ./pages/addpackage.md
---

---
src: ./pages/pinia.md
---

---
src: ./pages/msw.md
---


---
layout: end
---
