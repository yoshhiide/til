# 三項演算子のベターな書き方

airbnbを参考にした  
https://github.com/airbnb/javascript#15.6

```js
//better
const zoo = monkey > elephant
  ? true
  : false;

//best
const zoo = monkey > elephant ? true : false;
```

長くなるのであれば、関数化する方法も良さそう  
https://github.com/airbnb/javascript#8.5  

```js
//bad
const zoo = (animal) => animal.count > 200 ? true : false;

//good
const zoo = animal => { return animal.count > 200 ? true : false;};
```

goodの方を改行して使うのも良さそう  
```js
const zoo = animal => {
  return animal.count > 200
    ? true
    : false;
};
```

でも、arrow functionにするなら三項演算子をやめた方がもっと良さそう    
```js
const zoo = animal => {
  if (animal.count > 200) {
    return true;
  } else {
    return false;
  }
};
```