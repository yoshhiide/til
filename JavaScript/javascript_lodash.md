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


### minBy

最小値を持つ要素を取得することができる。

```js
const animals = [
    {
        name: 'monkey',
        count: 5
    }, {
        name: 'elephant',
        count: 9
    }, {
        name: 'snake',
        count: 4
    }, {
        name: 'horse',
        count: 7
    }, {
        name: 'kangaroo',
        count: 3
    }
];

_.minBy(animals, 'count');
// {name: "kangaroo", count: 3}
```



### groupBy

指定したキーやイテレータでグループ別に分別してくれる。  
配列内のオブジェクトにも対応している。 

```js
const animals = [
    {
        name: 'monkey',
        age: 5
    }, {
        name: 'snake',
        age: 9
    }, {
        name: 'snake',
        age: 4
    }, {
        name: 'monkey',
        age: 7
    }, {
        name: 'kangaroo',
        age: 3
    }
];
_.groupBy(animals, 'name');

// {'kangaroo': [{...}], 'monkey': [{...}], 'snake': [{...}]}
```



