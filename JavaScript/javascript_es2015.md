# 新しく覚えたES2015テクニック

### arrow functionの`()=>({})`の形でオブジェクトを返す

`{a:10, b:20, c:30}`  
を  
`[{a:10}, {b:20}, {c:30}]`  
に変換する。  
  
```js
_.map(obj, (val, key) => ({[key]: val}));
```

`=> ({})`のところを初めて使った。  
オブジェクトを返すわけだから、`() => {}`のみで良さそうに思ってしまったが、この形は`return`と書いて返さないといけないので、`()`で包むことで`return`と書かずにオブジェクトをそのまま返すことができる。  
ES2015のarrow functionの使い方としては知っていたが、実際に書くことに直面したことは初めてだった。  

