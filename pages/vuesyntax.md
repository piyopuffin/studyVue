---
level: 3
hideInToc: true
---
# <logos-vue /> 宣言的レンダリング
Vue.jsにおいて全ての基本になるのは、下のような単純な構文で、宣言的にデータをレンダリングすることです。

```vue
<div id="counter">
  Counter: {{ counter }}
</div>
```
```js
const Counter = {
  data() {
    return {
      counter: 0 //counterというプロパティを宣言する
    }
  }
}

// createApp()でVueインスタンスが生成され、.mount()で#counterにマウントされる。
// これによってDOMとVueインスタンス上のデータが相互にバインドできるようになる。
Vue.createApp(Counter).mount('#counter')
```

Vueインスタンス上のプロパティとDOM上にレンダリングされる内容はお互いをバインド（束縛）しています。

---
level: 3
hideInToc: true
---
# <logos-vue /> テンプレート構文

## テキスト展開
DOM側にdataで定義したプロパティのテキストを呼び出すテンプレート構文は主に下の2種類です。
- マスタッシュ構文 `{{ hoge }}`
  - 中にはJavaScriptを直接書くことができる（演算子、三項演算子など）ほか、関数の呼び出しも可能
  - 最終的にテキストとして出力される
- [v-htmlディレクティブ](https://ja.vuejs.org/guide/essentials/template-syntax#raw-html) `v-html="hoge"`
  - 最終的なデータがhtmlタグを含むものの場合、テキストではなくhtmlとして解釈され出力される。
  - [XSS](https://ja.wikipedia.org/wiki/%E3%82%AF%E3%83%AD%E3%82%B9%E3%82%B5%E3%82%A4%E3%83%88%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%97%E3%83%86%E3%82%A3%E3%83%B3%E3%82%B0)の脆弱性を生む可能性があるので、ユーザから渡されるデータを出力する場所では使用しないようにするなど、使い方には十分注意する。

```html
<!-- マスタッシュ構文 -->
<p>{{ button }}</p>
<p>{{ number + 1 }}</p>
```
```html
<!-- v-htmlディレクティブ -->
<p v-html="button"></p>
```
---
level: 3
hideInToc: true
---
# <logos-vue /> 属性のバインディング
HTML要素の属性とプロパティをバインドしたい場合は`v-bind`ディレクティブを使用する。
```html
<div v-bind:id="dynamicId">今日はいい天気だ。</div>
```

この例では、`dynamicId`プロパティの中身が変更されると、このHTML要素のid属性も同期して変化する。

例えば

```js
const dynamicId = ref('light')

const toggleDarkmode = ()=>{
  if(dynamicId.value === 'light'){
    dynamicId.value = 'dark'
  }else{
    dynamicId.value = 'light'
  }
}
```

のようにプロパティと関数が用意されている場合
html要素のid属性は、`toggleDarkmode()`が実行されるたびに
`id="light"`と`id="dark"`が切り替わる。

---
level: 3
hideInToc: true
---
# <logos-vue /> 属性のバインディング
## DEMO
<VBind />


---
level: 3
hideInToc: true
---
# <logos-vue /> クラスとスタイルのバインディング
プロパティに応じてhtmlのclass属性やstyle属性を変化させる

## クラスのバインディング `:class`

```html
<div :class="{active: isActive, 'text-danger': hasError}"></div>
```

上記のhtmlタグは`isActive`が`true`のとき`active`というクラスを、
`hasError`が`true`のとき`text-denger`というクラスを付加する。
通常のclass属性とも共存できる。
また、この場合はインラインで書いているが、js側のプロパティに書いて呼び出しても良い（objectを返す算出プロパティでもいい）。


---
level: 3
hideInToc: true
---
# <logos-vue /> クラスとスタイルのバインディング `:style`

## インラインスタイルのバインディング
```js
data() {
  return {
    activeColor: 'red',
    fontSize: 30
  }
}
```

```html
<div :style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
```

上の例では、JSの処理上でプロパティが変更されればDOM側のバインドされているスタイルのプロパティも連動して変更される。
インラインスタイルなので外部スタイルシートよりも適用優先度が高くなる点は注意。

---
level: 3
hideInToc: true
---
# <logos-vue /> 算出プロパティ　`computed`
リアクティブなデータを含むロジックに使用して、テンプレート上での複雑な計算を回避する
- Methodsの関数は再描画時に必ず再計算するが、Computedは使っているリアクティブなプロパティに変更がある時だけ再計算され、変更がない場合はキャッシュを使う。

例えばこのようにテンプレート上で三項演算子を使って表示を出し分けするようなものは、

```vue
<p>Has published books:</p>
<span>{{ author.books.length > 0 ? 'Yes' : 'No' }}</span>
```
このように算出プロパティに置き換えることができる。
```js
  import { ref, computed } from 'vue'
  const author = { books:[] }
  const publishedBooksMessage = computed(()=>{
    return author.value.books.length > 0 ? 'Yes' : 'No'
  })
```
```html
<template>
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
</template>
```


---
level: 3
hideInToc: true
---
# <logos-vue /> 条件付きレンダリング `v-if` `v-else`
- v-ifを付加したhtml要素は、条件式が`true`の時だけ描画される
- v-else-ifは2個目以降の条件式がある場合に使用する。条件式が`true`の時だけ描画される
- v-elseを付加したhtml要素は、直前のv-ifまたはv-else-ifが`false`の時だけ描画される

```js
import {ref} from 'vue'
const input = ref(null)
```

```html
<input v-model="input">

<p v-if="input === null">nullです</p>
<p v-else-if="/^[0-9]+$/.test(input)">数字です</p>
<p v-else-if="/^[A-Za-z]+$/.test(input)">英字です</p>
<p v-else>それ以外です</p>
```
<br>

> **v-ifがFALSEのときDOMはどうなるか**
> 
> 非表示ではなく、DOM要素そのものが消える。DOMは消したくないけど非表示にしたい（CSSでdisplay:none;した時みたいな感じ）ときはv-showを使う。

---
level: 3
hideInToc: true
---
# <logos-vue /> 条件付きレンダリング `v-if` `v-else`
## DEMO
<VIF />

---
level: 3
hideInToc: true
---
# <logos-vue /> リストレンダリング `v-for`
配列を利用した繰り返し描画ができるディレクティブ

`v-for="item in items"`のように要素に追加する。
このとき、itemsは参照する配列、`item`は配列に含まれる1つ1つのアイテム（エイリアス）を指している。`item`は任意の名前をつけることができ、呼び出したv-forのスコープ内だけで有効。

### プロパティの取り出しができる
```js
people:[{name:”hoge”, age:10},{name:”piyo”,age:12},{name:”fuga”,age:8}]
```
```html
<ul>
  <li v-for="person in people">名前：{{person.name}}　年齢：{{person.age}}歳</li>
</ul>
```
といった形でそれぞれのプロパティにアクセスできる。
<br><br>

> **v-ifとの相性**
> 
> 同じhtml要素に対してv-ifとv-forを同時に使うことはできない。v-ifをもった親要素の中にv-forの子要素を格納しよう。

---
level: 3
hideInToc: true
---
# <logos-vue /> イベントハンドリング `v-on`
DOMイベント（クリックなど）の購読ができるディレクティブ
- `v-on:click="sendMessage"` のように要素に追加する。
- @で省略して書くこともできる。`@click="sendMessage"`
- ハンドラーは直接js式を書いてもいいし、Methodsに書いておいて呼んでもいい。ちなみに直接式を書くのをインラインハンドラー、Methodsを呼ぶのをメソッドハンドラーという。覚えてなくても問題ない。


```js
data() {
  return {
    count: 0,
  }
},
methods:{
  countup: function(){
    this.count++
  }
}
```

```html
<button @click="count++">ボタン1</button>
<button @click="countup()">ボタン2</button>
{{ count }}
```
---
level: 3
hideInToc: true
---
# <logos-vue /> フォーム入力バインディング
v-model

フォーム上に入力された値とJS上の変数は同期させたい
inputイベントを拾ってリアクティブなプロパティを更新することもできるが、Vueではそれらを簡単に制御するためのv-modelディレクティブが備わっている。

下のような要素を作ると、inputに入力した内容がリアルタイムに`<p>`の内容を変更するので、リアクティブになっていることがわかる。
```js
data() {
  return {
    text: ''
  }
}
```

```html
<input v-model=”text”>
<p>{{text}}</p>
```

textarea、checkbox、radioなど色々なtypeでv-modelがどのように働くか確認しよう
---
level: 3
hideInToc: true
---
# <logos-vue /> ウォッチャー
プロパティ変更の監視

watchメソッドを使用してプロパティの変更を検知し、処理を実行する
```js
export default {
  data() {
    return {
      question: '',
      answer: '?を付けて質問してね'
    }
  },
  watch: {
    question(newQuestion, oldQuestion) {// 質問内容が変更されるたびにgetAnswer()を実行
      if (newQuestion.includes('?')) {
        this.getAnswer()
      }
    }
  },
  methods: {
    async getAnswer() {
      this.answer = '考え中...'
      try {
        const res = await fetch('https://yesno.wtf/api')
        this.answer = (await res.json()).answer
      } catch (error) {
        this.answer = 'エラー：APIにアクセスできません' + error
      }
    }
  }
}
```

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
# <logos-vue /> ref属性
DOM要素を直接指定する

JS側から特定のDOM要素を直接指定して制御したい場合、ref属性を使用することができる。
HTML側でref属性で名前を定義しておき、JS側から`this.$refs.名前`でアクセスできる。

DOM側
```html
<input ref="input">
```

JS側
```js
this.$refs.input.focus();
```

上の例では、 `ref=”input”`の要素にフォーカスを移している。

注意：<br>
DOM要素へのアクセスはレンダリングが終わってからでないとできない。refを使ってDOMにアクセスする場合は、実行時のライフサイクルがmounted以降である必要があることに注意しよう。