# Method functional cache

Node.js v6.9.0  

Array.prototypeメソッドなどで、その引数となるCallbackをそのまま引数内に書くか、関数宣言して書くか、どちらが早いのか検証した。  
関数宣言する場合は、ループの外に置くようにした。  
この場合に関数を探しに行くコストと一度読み込ませているというキャッシュの効果が結果に影響するのかを検証したかった。  

  
```js
// 結果
/*
loop: 4.830ms
func: 2.612ms

loop: 4.753ms
func: 2.718ms

loop: 8.216ms
func: 2.716ms

loop: 4.948ms
func: 3.190ms

loop: 4.512ms
func: 2.721ms
*/
```
  
```js
const arr = [
  {ac:10,name:'nezumi'},
  {ac:20,name:'ushi'},
  {ac:30,name:'tora'},
  {ac:40,name:'usagi'},
  {ac:50,name:'dragon'},
  {ac:60,name:'snake'},
  {ac:70,name:'horse'},
  {ac:80,name:'sheep'},
  {ac:90,name:'dog'},
  {ac:100,name:'inoshishi'},
  {ac:110,name:'cat'},
  {ac:120,name:'elephant'},
  {ac:130,name:'kirin'},
];

const race1 = () => {
  console.time('loop');
  for (let i = 0; i<10000; i++) {
    const found = arr.some(animal => animal.name === 'elephant');
    if (found) continue;

  }
  console.timeEnd('loop');
};


const race2 = () => {
  console.time('func');
  const matchAnimal = (animal) => animal.name === 'elephant';
  for (let i = 0; i<10000; i++) {
    const found = arr.some(matchAnimal);
    if (found) continue;

  }
  console.timeEnd('func');
};

Promise.resolve(true)
  .then(() => Promise.all([
    race1(),
    race2(),
  ]))
  .then(() => console.log('end.'));
```