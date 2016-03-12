# Promise

Node.js v5.8.0  

うまくいくのか不安になったので検証した。  

下記コードの`sub`は`Promise`で包まなくても問題ないか検証。  
当然のように成功した。  

```js
'use strict';

const main = () => {
  return new Promise((resolve, reject) => {
    resolve(true);
  });
};

const sub = () => {
  return main();
};

const func = () => {
  return new Promise((resolve, reject) => {
    sub()
      .then(() => resolve(true))
      .catch(() => reject(false));
  });
};

func()
  .then(() => console.log('then'))
  .catch(() => console.log('catch'));
```


こちらも試してみて成功した。

```js
'use strict';

const main = (ms) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve(true);
      //reject(true);
    }, ms)
  });
};

const sub = (ms) => {
  return new Promise((resolve, reject) => {
    main(ms)
      .then(() => resolve(true))
      .catch(() => reject(false));
  });
};

const func = (arg) => {
  const ms = arg + 1000;
  return sub(ms);
};

func(1500)
  .then(() => console.log('then'))
  .catch(() => console.log('catch'));
```