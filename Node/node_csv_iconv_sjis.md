# Shift-jisのCSVをiconv-liteを使って出力

`iconv`だとPythonのバージョンの影響があって環境によってはインストールできないこともある(主に顧客SV)  
なので、sjis変換には`iconv-lite`を利用する。  

他には`json2csv`を使って、jsonをcsvに変換してもらう。  

```js
'use strict';

const fs = require('fs');
const json2csv = require('json2csv');
const iconv = require('iconv-lite');

const fields = ['monkey', 'snake'];
const fieldNames = ['サル', 'ヘビ'];

const data = [{monkey: 1, snake: 2}, {monkey: 'saru', snake: 'ヘビ'}];

json2csv({data, fields, fieldNames}, (err, csv) => {
  if (err) {
    console.log(err);
  }
  console.log(csv);
  const savecsv = iconv.encode(csv, 'shift_jis');
  fs.writeFileSync('out.csv', savecsv);
});
```
