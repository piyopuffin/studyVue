---
level: 4
---
# <logos-vue /> MSW（Mock Service Worker）
APIをモックできる開発環境用プラグイン

実際のプロダクト開発ではバックエンド（API）から取得したデータをフロントエンド側で利用することになる。しかしフロントエンドの開発時にAPIがまだ出来上がっていないことも多く、APIの完成を待っているとなかなかフロントエンドのデバッグができない。そこで、APIモックが生まれた。

MSW（Mock Service Worker）は、ブラウザ上のリクエストをインターセプトして擬似APIのように動くサービスワーカーから値を返すことができる。

https://mswjs.io/docs/getting-started/install

<p style="font-size:12px;">開発のためのツールなので、npm installするときは-Dオプションをつけて開発環境のみに追加しよう。</p>