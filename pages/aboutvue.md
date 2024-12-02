---
level: 3
---
# <logos-vue /> Vue.jsとは？

## JavaScriptのフレームワークの1つである
JavaScriptはご存知の通りWebブラウザ上で動作させるために開発されたスクリプト言語である。今はどんなWebページでもほぼ何かしらのJSが動いている。

バニラなJavaScriptでも、やろうと思えば大抵なんでも実装はできてしまう。しかし開発効率を考えると、それはあまり理想的ではない（勉強目的であれば、バニラJS縛りで実装することで得るものはあり、必ずしも悪いことではない）。すべてを自分で作るのではなく、利用できる部分では先人が作ったものを利用して、サービス固有の機能の開発により時間を使いたいと思うのは自然の道理である。

フレームワークはこのように、元々のまっさらなプログラミング言語・スクリプトに対して、必要な機能・よく使う機能がすでに備えられた状態の「骨組み」である。


>「フレームワーク」と「ライブラリ」の違い
>
> 単語が図書館（Library）であることから想像できるように、ライブラリは便利なプログラムを集めたものである。あくまでも1個1個の部品の集まりであり、システムの骨組みとしての機能はない点がフレームワークとの違いである。図書館で集められているたくさんの本から目的の本を探して読めるように、プログラムにおけるライブラリでもその中に所蔵されている便利なプログラムを呼び出して使うことができる。

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
h2{
  padding-left: 0.4em;
  border-left: 0.3em solid #40b883ff;
}
</style>
---
level: 3
hideInToc: true
---
# <logos-vue /> Vue.jsとは？
フロントエンド開発を目的に作られたJavaScriptのフレームワークの1つ

JavaScriptをベースとしたフレームワークとしては、先にGoogleが中心となって開発された[AngularJS（現：Angular）](https://angular.dev/)があった。Vue.jsを作ったEvan You氏は元々このAnglarJSの開発者であり、「AngularJSの好きなところだけを抜き出した軽いフレームワークが作れるのではないか」と考えVue.jsが生まれた。

> 現在はAngular・React・Vue.jsが三大SPAフレームワークと呼ばれている（らしい）

<hr style="margin: 1em 0">

#### Node.jsとは？

Node.jsの元であるJavaScriptは、Webブラウザの上で動くスクリプト言語である。基本的にはWEBブラウザ上にある情報にしかアクセスの権限はなく、セキュリティ上OSの機能に直接アクセスすることはできない。
そこでOS上でJavaScriptを動作させるためのJavaScriptランタイムとして開発されたのがNode.jsである。


> ブラウザ上で動くスクリプトからOSの機能に直接アクセスできてしまうと、Webサイトの開発者がページの閲覧者の端末を操作できてしまうため、原則的にwebページ上にあるJavaScriptはそれが許されない。ただし、最近ではWebブラウザがスクリプトとOSとの間を取り持つようになってきており、ユーザの許可を得た上であれば間接的にOSの一部の機能にアクセスできるようになっている。（カメラの起動、位置情報の取得 など）

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
h2{
  padding-left: 0.4em;
  border-left: 0.3em solid #40b883ff;
}
</style>
---
level: 3
hideInToc: true
---
# <logos-vue /> Vue.jsとは？
## 双方向性バインディングができる
本来スクリプト上の変数とレンダリングされたDOMの間には何も関連性がない。しかしモダンな開発において高度な実装が必要になるにつれ、その点はもどかしいところだった。開発者の中で「変数に格納される値に応じて、DOMにレンダリングされる内容も変わってくれたらいいなぁ...」こういう需要が生まれるのは必然だった。

そこで登場したのが双方向性バインディングである。

変数に変更を加えると、レンダリングされる内容も変わる。これはVue.jsよりもっと古くからあるJSライブラリのbackbone.jsが発明した画期的なアイディアだった。逆に、ユーザがレンダリングされた画面上で何かデータの変更を行うと、Vue.jsの中の関連する変数も更新される。これが双方向性の指すところである。
双方向（変数からDOM、DOMから変数の両方）でデータをバインド（結びつけ）する。

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
h2{
  padding-left: 0.4em;
  border-left: 0.3em solid #40b883ff;
}
</style>
---
level: 3
hideInToc: true
---
# <logos-vue /> Vue.jsとは？
## 仮想DOMを使っている
前ページで述べた通り、双方向性バインディングは画期的アイデアだった。
しかしある時、「レンダリングされたDOMに対していちいち読み書きを行うのはパフォーマンスが悪く遅い。できるだけ読み書きの回数を抑えたい」という考えが生まれた。速度はスクリプト言語において重要なファクターだった（今もね）。

構築するべきDOMとその直前の状態のDOMに対応したJSのObjectがあれば、この差分を求めて書き込みを行うのは比較的簡単なのでは？というアイデアが生まれた。仮想DOMの誕生である。

Vue.jsではこの仮想DOMをインメモリに持つことでレンダリングすべきDOMの状態を管理している。
（正直ここまではJSベースのモダンなSPA技術は全部同じ系譜なので、ReactとかAngularとかも同じはなし。）

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
h2{
  padding-left: 0.4em;
  border-left: 0.3em solid #40b883ff;
}
</style>

---
level: 3
hideInToc: true
---
# <logos-vue /> Vue.jsとは？
## .vueというファイル拡張子が使える
Vue.jsは.vue拡張子のファイルを読み込むことができる機能がある。このファイルは単一ファイルコンポーネント（SFC）と呼ばれる。

その中身には、scriptタグ、templateタグ、styleタグを含めることができる。.vue内にそれらのタグがあるとき、Vue.jsは内部的に、それぞれをJavaScript、HTML、CSSとして扱うことになっている。

.vueファイルはJavaScriptにコンパイルされる必要がある。しかし、Vue.jsの利点を最大限活かすためには単一コンポーネントが必要となる。
単一ファイルコンポーネントを使用すると、共通パーツを作っていろんなページで呼び出し、再利用できる。（呼び出す側を親といったり、呼び出される側を子と言ったりもする）

※ちなみに単一ファイルコンポーネントはCDN版では使うことができない。

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
h2{
  padding-left: 0.4em;
  border-left: 0.3em solid #40b883ff;
}
</style>
---
level: 3
hideInToc: true
---
# <logos-vue /> Vue.jsとは？
## まとめ
このような成り立ちはVue.jsの仕様を把握する上で役に立つが、Vue.jsに少し習熟してから調べるとより理解が深まると思うので軽く触れるに留めておく。次頁からは、実際にVue.jsに触ってみる。


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
h2{
  padding-left: 0.4em;
  border-left: 0.3em solid #40b883ff;
}
</style>