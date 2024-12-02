---
level: 3
layout: two-cols
---
# <logos-vue /> ライフサイクル
##
Vue.jsのインスタンスには[ライフサイクル](https://ja.vuejs.org/guide/essentials/lifecycle.html#registering-lifecycle-hooks)がある。

インスタンスは生成〜破棄までのライフサイクルの中に幾つかのライフサイクルフックという関数があり、ライフサイクルフックにはユーザが任意のコードを追加することができる。

https://ja.vuejs.org/api/options-lifecycle.html

https://swallow-incubate.com/archives/blog/20190422/

::right::

<img src="/assets/images/lifecycle.png" class="ml-10 w-70 h-auto" />

---
level: 3
hideInToc: true
---
# <logos-vue /> ライフサイクルフック
## ①Vueインスタンスの生成（初期化）
発生フック： beforeCreate、created

```vue
<template>
  {省略}
</template>
<script>
export default{
  beforeCreate() {
    // リアクティブデータ作成前に行いたい処理
  },
  created() {
    // リアクティブデータ作成後に行いたい処理
  }
}
<script>
```

Vueインスタンスが生成されたタイミング（つまり`new Vue()`された時）に、まず2つにフックが呼び出されます。

<p style="font-size:12px;">
  beforeCreate：リアクティブデータが初期化される直前<br>
  created：リアクティブデータが初期化された直後<br>
  ※まだDOMは反映されていないタイミングのため、まだDOMにアクセスはできないことに注意
</p>

<style>
.slidev-code{
  font-size: 10px !important;
  line-height: 1.3 !important;
}
</style>

---
level: 3
hideInToc: true
---
# <logos-vue /> ライフサイクルフック
## ②DOMへのマウント
発生フック： beforeMount、mouted

```vue
<template>
  {省略}
</template>
<script>
export default{
  beforeMount() {
    // DOMにマウントされる前に行いたい処理
  },
  mounted() {
    // DOMにマウントされた後に行いたい処理
  }
}
<script>
```

次にDOMへのマウントが始まります。これによってvueコンポーネントがHTML要素の一員として画面に描画されます。
<p style="font-size:12px;">
  beforeMount：DOMにマウントされる直前<br>
  mounted：DOMにマウントされる直後
</p>

<style>
.slidev-code{
  font-size: 10px !important;
  line-height: 1.3 !important;
}
</style>

---
hideInToc: true
---
# <logos-vue /> ライフサイクルフック
## ③データ変更／画面の更新
発生フック： beforeUpdate、updated

```vue
<template>
  {省略}
</template>
<script>
export default{
  beforeUpdate() {
    // DOMが更新される前に行いたい処理
  },
  updated() {
    // DOMを更新した後に行いたい処理
  }
}
</script>
```

vueインスタンスのdataが変更されたり、親が渡すpropsに変化があったとき、
その変更のタイミングでDOMは自動的に更新（再描画）されます。
<p style="font-size:12px;">
  beforeUpdate：DOMを更新する直前<br>
  updated：DOMを更新した直後
</p>

<style>
.slidev-code{
  font-size: 10px !important;
  line-height: 1.3 !important;
}
</style>
---
hideInToc: true
---
# <logos-vue /> ライフサイクルフック
## ④Vueインスタンス破棄
発生フック： beforeDestroy、destroyed

```vue
<template>
  {省略}
</template>
<script>
export default{
  beforeDestroy() {
    // Vueインスタンスを破棄する前に行いたい処理
  },
  destroyed() {
    // Vueインスタンスを破棄した後に行いたい処理
  }
}
<script>
```

`v-if`や`v-for`、`router.push`などでインスタンスが破棄されるタイミングでフックされます。
<p style="font-size:12px;">
  beforeDestroy：DOMを破棄する直前<br>
  destroyed：DOMを破棄した直後
</p>