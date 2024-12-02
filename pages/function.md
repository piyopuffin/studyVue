---
level: 3
transition: fade-out
---
# <logos-javascript /> 関数（再利用可能なコードの集合体）
関数を作ると、実行したいコードの塊を定義でき、別の場所から呼び出したりして再利用することができます。
```js
function Double(num){
  const result = num*2;
  return result;
}


//呼び出し
const i = 50;
console.log(Double(i));

//コンソールの出力 -> 100

```