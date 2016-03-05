# ディープマージできるmergeパッケージ

`npm install --save merge`

## マージする対象がundefinedやfalseの場合の挙動

```js
'use strict';

const merge = require('merge');

const a = {zoo: {monkey: 10, elephant: 20}};
const b = false;
const c = undefined;

const m1 = merge.recursive(true, a, b);
console.log(m1);
// { zoo: { monkey: 10, elephant: 20 } }

const m2 = merge.recursive(true, a, c);
console.log(m2);
// { zoo: { monkey: 10, elephant: 20 } }
```

## 空の配列をマージすると空の配列になる

```js
const a = {zoo: ['monkey', 'elephant']};
const b = {zoo: []};

const m1 = merge.recursive(true, a, b);
console.log(m1);
// { zoo: [] }
```