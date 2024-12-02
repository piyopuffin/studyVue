---
level: 3
---
# <logos-javascript /> 条件文
`if(条件式A){条件式Aがtrueのとき実行}else if(条件式B){条件式Bがtrueのとき実行}else{どの条件も当てはまらないとき実行}`


```js
const age = 17;

if(age < 18){
  console.log(“あなたは18歳未満です”);
}else if(age < 20){
  console.log(“あなたは18歳以上20歳未満です”);
}else{
  console.log(“あなたは20歳以上です”);
}

```
<br>

> - else ifは複数あっても良い
> - 条件Aを満たしたら、条件Bは満たしていても実行しない