---
level: 3
---
# <logos-vue /> コンポーネント
再利用可能なパーツをうまく使ってアプリケーションを構築する

再利用とは、同じファイルをいろんな場所で使い回すことである。通常、HTMLとCSSだけで画面構築する場合、複数ページにまたがって全く同じパーツ（例えばheaderとかfooterとか）が表示される場合でも、それぞれのHTMLに同じ記述を書く必要がある。
しかし、.vueファイルは別の.vueファイルをコンポーネントとして読み込んで利用することができる。

<div class="flex">
  <div class="bg-slate-100 pa-4 mr-4">
    <h4 class="mb-2"><logos-vue />index.vue</h4>
    <div class="bg-slate-200 pa-2 mb-2">Header.vueを呼び出し</div>
    <div class="bg-slate-200 pa-2 mb-2">index.vue 独自のコンテンツ</div>
    <div class="bg-slate-200 pa-2">Footer.vueを呼び出し</div>
  </div>
  <div class="mr-4">
    <div class="bg-slate-100 pa-4 mb-4">
      <h4><logos-vue />Header.vue</h4>
    </div>
    <div class="bg-slate-100 pa-4">
      <h4><logos-vue />Footer.vue</h4>
    </div>
  </div>
  <div class="bg-slate-100 pa-4">
    <h4 class="mb-2"><logos-vue />news.vue</h4>
    <div class="bg-slate-200 pa-2 mb-2">Header.vueを呼び出し</div>
    <div class="bg-slate-200 pa-2 mb-2">news.vue 独自のコンテンツ</div>
    <div class="bg-slate-200 pa-2">Footer.vueを呼び出し</div>
  </div>
</div>

---
level: 3
hideInToc: true
---
# <logos-vue /> 再利用可能なコンポーネント

<div class="flex">
  <div class="bg-slate-100 pa-4 mr-4">
  <h3><logos-vue /> 呼び出す側（親）の書き方</h3>
```vue
<script>
import News from './components/NewsArticle.vue';
</script>

<template>
 <header>これはヘッダーです</header>
 <News />
 <main>
    メインコンテンツ
 </main>
</template>
```
</div>

<div class="pa-2">
script内でコンポーネントをimportする必要がある。この時コンポーネント名を任意の名前で宣言することができる。
template側で＜宣言した名前  /＞`で呼び出すことができる。ちなみにtemplate内で何回呼び出してもいい。
呼び出したコンポーネントに対し、呼び出し側からデータを渡すこともできる。これをpropsという。

```html
<News title="今日の天気" content="今日はいい天気でした！" /> 
```

このように静的データを渡すことができる。ただし実際の開発の場面ではAPIから取得した動的なデータを渡したいことの方が多いはず。その場合は、

```html
<News :title="title" :content="content" />  
```
このように半角コロンをつければ、プロパティをpropsで渡すことができる。このときpropsの名称は任意に決めることができる。
</div>

</div>

---
level: 3
hideInToc: true
---
# <logos-vue /> 再利用可能なコンポーネント

<div class="flex">
  <div class="bg-slate-100 pa-4 mr-4">
  <h3><logos-vue /> 呼び出す側（子）の書き方</h3>

```vue
<script setup>
export default {
  props: ['title','content']//親から渡されたpropsで使うものを宣言
}
</script>

<template>
 <article>
    <h3>{{ title }}</h3>
    <p>{{ content }}</p>
 </article>
</template>

```
</div>

<div class="pa-2">
呼び出されるだけであれば、子側は特に何もしなくても良い。ただし、親からpropsを渡されていて、そのpropsを利用したいときは書き方があるので説明する。

親側で
```html
<Sidebar title="ABCD" />  
```
このように親から渡されたpropsは、子側でも「このpropsを使います」と宣言する必要がある。
宣言した後は、通常のプロパティと同じようにtemplate内でマスタッシュ構文で呼び出したりできる。
</div>

</div>

---
level: 3
hideInToc: true
---
# <logos-vue /> 再利用可能なコンポーネント

<div class="flex">
  <div class="bg-slate-100 pa-4 mr-4">
  <h4><logos-vue /> 親は子のイベントを購読して処理を行う</h4>

```vue
<script>
export default {
  data() { 
    return {
      posts: [ /* ... */ ],
      postFontSize: 1 
    }
  }
}
</script>
<template>
  <div :style="{ fontSize: postFontSize + 'em' }">
    <BlogPost @enlarge-text="postFontSize += 0.1"/>
  </div>
</template>
```

<h4><logos-vue /> 親は子のイベントを購読して処理を行う</h4>
```vue
<template>
  <button @click="$emit('enlarge-text')">文字を大きく</button>
</template>
```
</div>

<div class="pa-2">
親は子のイベントを購読することもできる。子から親へイベントを渡すことをemitという。

宣言した後は、通常のプロパティと同じようにtemplate内でマスタッシュ構文で呼び出したりできる。

</div>

</div>

<style>
.slidev-code{
  font-size: 10px !important;
  line-height: 1.3 !important;
}
</style>