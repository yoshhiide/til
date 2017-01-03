# process.nextTick

## Promiseは非同期にならない

Promiseを使っても、最初のPromiseは非同期になっていない。  
then以降が非同期になる。  

下記の例で非同期になっていない様子がわかる。  

```js
const promiseWhile = () => {
  return new Promise((resolve) => {
    let i = 0;
    while(true) i++;
    resolve(true);
  });
};
promiseWhile();
console.log('this is async.');

// (何も出力されない)
```
  
## then以降は非同期処理される

上記例を一部修正して、promiseWhile()を.thenでつないだ後に実行する。  
  
```js
const promiseWhile = () => {
  return new Promise((resolve) => {
    let i = 0;
    while(true) i++;
    resolve(true);
  });
};
const promise = () => {
  return new Promise((resolve) => {
    resolve(true);
  });
};
promise().then(promiseWhile);
console.log('this is async.');

// this is async.
```

`then`以降は非同期になっていることがわかる。  
  
## process.nextTick

`while`を`process.nextTick`で処理する。  

```js
const promiseWhile = () => {
  return new Promise((resolve) => {
    let i = 0;
    process.nextTick(() => {
      while(true) i++;
    });
    resolve(true);
  });
};

promiseWhile().then(() => console.log('then.'));
console.log('this is async.');

// this is async.
```

最初のPromise内で`process.nextTick`でループを処理することで、非同期に処理してくれるようになった。  
  
## 連続するprocess.nextTickの処理

Promise外でも`process.nextTick`で処理をする。  

```js
const promiseWhile = () => {
  return new Promise((resolve) => {
    let i = 0;
    process.nextTick(() => {
      for (; i < 500000000; i++) {
        i = i;
      }
      console.log('for loop1 end.');
    });
    resolve(true);
  });
};

promiseWhile().then(promiseWhile).then(() => console.log('then.'));
console.log('this is async1.');
process.nextTick(() => console.log('nextTick2.'));
console.log('this is async2.');

// this is async1.
// this is async2.
// for loop1 end.
// nextTick2.
// then.
```
  
`process.nextTick`内での処理が同期処理である場合は、終了するまで次の`process.nextTick`は実行されない。  

## process.nextTick内を非同期処理にする

次の例では、`process.nextTick`内での処理を非同期処理にしている。  

```js
const promise = () => {
  return new Promise((resolve) => {
    process.nextTick(() => {
      setTimeout(() => {
        resolve(true);
        console.log('promise setTimeout end.');
      }, 5000);
    });
  });
};

promise().then(() => console.log('then.'));
console.log('this is async1.');
process.nextTick(() => console.log('nextTick2.'));
console.log('this is async2.');

// this is async1.
// this is async2.
// nextTick2.
// promise setTimeout end.
// then.
```

`process.nextTick`内での処理が非同期処理であれば、その処理が完了するまで待たずに次の`process.nextTick`で行われる処理が開始される。  
  
  
最初のPromiseで重たい処理をするのであれば、`process.nextTick`で処理をさせることが良さそうだが、最後の例のように`process.nextTick`の内部でもPromiseを使って非同期処理とする方が良さそう。  

