# Node.jsでD3.jsで描画したものをPNGファイルにして出力

サーバサイドで完結する形の図をPNGにしたくてやってみた。  

### 環境
OSX 10.11.3  
Node.js v5.7.1

### d3以外の使ったモジュール  
[jsdom - https://www.npmjs.com/package/jsdom](https://www.npmjs.com/package/jsdom)
[svg-to-png - https://www.npmjs.com/package/svg-to-png](https://www.npmjs.com/package/svg-to-png)

`npm install --save d3 jsdom svg-to-png`  

### 参考になったサイト
https://bl.ocks.org/tomgp/c99a699587b5c5465228
https://gist.github.com/Caged/6407459
http://fits.hatenablog.com/entry/2016/02/22/012432

### ハマったこと
jsdomが新しいとダメなのか、サーバサイドでD3.jsを描画するところでなかなかうまくいかなかった。  
参考になったサイトの3番目の日本語のブログ(最近の記事)に助けられた。  

### 概要
円グラフ(パイチャート)を描画し、一旦、SVGに保存。  
SVGをPNGに変換して保存する。  

### コード
index.js

```js
'use strict';

const fs = require('fs');
const path = require('path');
const d3 = require('d3');
const jsdom = require('jsdom').jsdom;
const svg_to_png = require('svg-to-png');

const pie = d3.layout.pie();
const arc = d3.svg.arc().innerRadius(0).outerRadius(100);
const document = jsdom();

const viewPie = d3.select(document.body)
.append('svg')
.attr({
  xmlns: 'http://www.w3.org/2000/svg',
  width: 400,
  height: 300
})
.selectAll('path')
.data(pie([35, 20, 15, 7, 23]));

viewPie.enter()
  .append('path')
  .attr({
    'class': 'pie',
    'd': arc,
    'transform': 'translate(200, 150)'
  })
  .style('fill', (d, i) => ['blue', 'yellow', 'red', 'white', 'green'][i]);

fs.writeFileSync('pie.svg', document.body.innerHTML);
svg_to_png.convert(path.resolve('pie.svg'), 'pie.png');
```


### 実行

`node index.js`  

モジュールの仕様なのか、`./pie.png/pie.png`に作られた。