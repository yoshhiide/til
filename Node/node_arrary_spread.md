# array spread

Node.js v6.9.4  

配列に入ったデータを各変数に割り振りたい時に、配列が途中からある場合にどのようにセットしたら良いか考えていた。  

  
`const data = ['山田', '30', '東京', 'トマト', 'りんご', 'パン'];`


下記のように一つずつセットするのは面倒

```js
const name = data[0];
const age = data[1];
const area = data[2];
const likes[0] = data[3];
const likes[1] = data[4];
const likes[2] = data[5];
```
  
まとめてセットする  

```js
const [name, age, area, ...likes] = data;
```