---
level: 3
---
# <logos-javascript /> 比較演算子
- a == b
  - 等価演算子。両者を比較して等しければ`true`、そうでなければ`false`を返す。
  - 値のみが等しければよく、型は見ない。`0 === "0"`は`true`となる。
- a === b
  - 厳密等価演算子。両者を比較して等しければ`true`、そうでなければ`false`を返す。
  - 値も型も同じでなければならない。`0 === "0"`は`false`となる。
- a !== b
  - 値か型のいずれかが異なると`true`を返す。
- a != b
  - 値が異なれば`true`を返す。

<br>

> 注意<br>null == undefined は、値も型も異なるが`true`になる

---
level: 3
hideInToc: true
---
# <logos-javascript /> 比較演算子
- a < b
  - aよりbの値が大きければ`true`を返す。
- a <= b
  - aがb以下ならば`true`を返す。
- a > b
  - aよりbの値が小さければ`true`を返す。
- a >= b
  - aがb以上ならば`true`を返す。 
