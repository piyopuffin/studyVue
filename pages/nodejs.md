---
level: 3
---
# <logos-vue /> Node.jsのインストール
## Homebrew をインストールする
インストールの仕方は[こちら](https://brew.sh/ja/)を参照してください。

## nodebrewでnodeをインストールする
```bash
$ brew install nodebrew
```
※nodeがインストール済みだとうまくいきません。

```bash
$ nodebrew -v
```
でバージョンが表示されればnodebrewがインストールされています。

次に、.bash_profile にパスを通します。デフォルトのシェルがzshの人の場合は.zshrcになります

```
export PATH=$HOME/.nodebrew/current/bin:$PATH
```

<style>
  h2{
  padding-left: 0.4em;
  border-left: 0.3em solid #40b883ff;
  }
</style>
---
level: 3
hideInToc: true
---
# <logos-vue /> Node.jsのインストール
ソースを適用します。これもデフォルトシェルがzshの場合は.zshrcになります
```bash
source ~/.bash_profile
```

セットアップします。
```bash
nodebrew setup
```

インストール可能なnodeのバージョンを確認
```bash
nodebrew ls-remote
```

nodeをインストール（さっきのバージョン確認したときにでた最新でいいと思います）
```bash
nodebrew install-binary <version>
```
使うnodeのバージョンを設定
```bash
nodebrew use <version>
```