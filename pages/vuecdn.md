---
level: 3
---
# <logos-vue /> CDNで基本的な機能を体験する
Option APIとComposition API

Vue3では、Vue2までの標準方式だったOptions APIに加え、Composition APIという新しいコンポーネント形式が使えるようになっている。

ただ、Composition APIはJavaScriptに習熟していて大きなシステムを作る人にとっては大きなメリットがある（関心事を分離して記述でき、コードの整理がしやすかったりする）が、初学者の段階だと逆にVue.jsの基本思想が理解しにくい場合もある。
本資料はVue3でComposition APIを使う前提で書かれているということに留意いただきたい。

---
level: 3
hideInToc: true
---
# <logos-vue /> CDNで基本的な機能を体験する
installation

CDNを使うとビルド不要で簡単にVue.jsの機能を体験できる。CDN版ではできないこともあるが、感覚を掴む最初のステップとして今回はCDNでVue.jsを体験しよう。

- index.htmlのheadタグ内で、vueのCDNを読みこむ 
```html
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```

- bodyタグ内に、id="app"のdivタグを作る
- main.jsを作成し、bodyの閉じタグ直前で、main.jsを読み込む

```html
...
<head>
  ...
  <script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
</head>
<body>
  <div id="app"></div>
  <script src="main.js"></script>
</body>
...
```
---
level: 4
---
# <logos-vue /> アプリケーションの作成
- VueからcreateAppをインポートする
- createAppメソッドを使って、新しいVueインスタンスを作成する。
  - #appをマウント先として指定する。
- setupメソッドの中でリアクティブなプロパティ等を宣言する
- テンプレート側で使用したいプロパティやイベントリスナー等はreturnする

```js{1|3|10|4,5,6,7,8,9}
const { createApp, ref } = Vue

Vue.createApp({
  setup() {
    const message = ref("Hello Vue.js!")
    return {
      message
    }
  }
}).mount('#app')
```

---
src: ./vuesyntax.md
---