# lodash

よく使っているlodashについて初めて使って便利だったもの  

### findKey

オブジェクトの中のkey-valueオブジェクトや、配列の中のオブジェクトから探索する為に使うケースはあったが、今回、１つのオブジェクトから条件に一致する値を持つキーを探索する為に使った。  

```js
const zoo = {
    '234': '0192020',
    '123': '1290384',
    '190': '7039001',
    '729': '4209898'
};
_.findKey(zoo, v => v === '7039001');
// '190'
```

### unset, remove, pull, without

オブジェクトや配列から特定の要素を削除する場合に便利なもの。  

`_.unset()`はオブジェクトから指定要素を削除できるが、配列には対応していない。  
他は配列にのみ対応する。  
`_.without()`に限っては、元々の配列に副作用を与えず、新しい変数に代入できる。

```js
const zoo = {
    'tokyo'   : 'ueno',
    'hokkaido': 'asahiyama',
    'ooita'   : 'takasakiyama'
};
const animals = ['monkey', 'elephant', 'snake', 'horse', 'kangaroo'];

// オブジェクト
_.unset(zoo, 'tokyo');

// 配列
_.remove(animals, a => a === 'horse');

_.pull(animals, 'monkey', 'kangaroo');

const animals2 = _.without(animals, 'snake');
```