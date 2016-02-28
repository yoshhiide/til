# 関数

関数は`def`で定義する。  
`def function_name(a, b):`といった形式で記述する。  
  

## 関数の引数

関数の引数に`*`を頭につけ、`*arg`のようにすると、複数の引数をタプルで取得できる。  

```python
>>> def func(*arg):
...  print(type(arg))
...  print(arg)
... 
>>> func(1,2,3,4)
<class 'tuple'>
(1, 2, 3, 4)
```

同様に引数の頭に`**`で`**arg`とすると、関数呼び出し時のキーワード引数を辞書として取得できる。  

```python
>>> def func(**arg):
...  print(type(arg))
...  print(arg)
... 
>>> func(no=123, age=20, name='yoshihide')
<class 'dict'>
{'name': 'yoshihide', 'no': 123, 'age': 20}
```

上記ふたつ(`*`と`**`)を組み合わせても、別々にうまく認識してくれる。  

```python
>> def fun(*arg, **kw):
...  print(arg)
...  print(kw)
... 

# 失敗例
>>> fun(id=123,1,2,3)
  File "<stdin>", line 1
SyntaxError: non-keyword arg after keyword arg

# 適切例
>>> fun(1,2,3)
(1, 2, 3)
{}

>>> fun(id=123)
()
{'id': 123}

>>> fun(1,2,3,id=123)
(1, 2, 3)
{'id': 123}
```

## ラムダ関数

ラムダ関数は、ひとつの文で表現できる無名関数。  

ラムダ関数で書かない場合  

```python
>>> def dofunc(arg, func):
...  for x in arg:
...   print(func(x))
... 
>>> def add10func(a):
...  return 10 + a
... 
>>> dofunc([1, 2, 3], add10func)
11
12
13
```

ラムダ関数で書いた場合  

```python
# 上記例を書き直した場合
>>> dofunc([1, 2, 3], lambda a: a + 10)
11
12
13
```

## ジェネレータ関数

ジェネレータはメモリに格納しなくても処理できる。  
ジェネレータ内包表記に書くには長くなる場合に、ジェネレータ関数を書く。  
ジェネレータ関数では、`return`の代わりに`yield`を使う。  
```python
>>> def genfunc(*arg):
...  for x in arg:
...   yield x
... 

>>> genfunc
<function genfunc at 0x1054e41e0>

>>> res = genfunc(1,2,3,4)
>>> res
<generator object genfunc at 0x105488288>

>>> print(list(res))
[1, 2, 3, 4]

>>> print(list(res))
[] 
```

## デコレータ

デコレータは引数として関数をひとつ取り、別の関数を返す関数。  

```python
>>> def decfunc(func):
...  def resfunc(*args, **kwargs):
...   return func(*args, **kwargs)
...  return resfunc
... 
>>> def add_ints(a , b):
...  return a + b
...

>>> func1 = decfunc(add_ints)
>>> func1(3, 4)
7
```

デコレートしたい関数の直前に`@関数名`と記述することで、その関数の動作が得られる。  

```python
>>> def decfunc(func):
...  def resfunc(*args, **kwargs):
...   return func(*args, **kwargs)
...  return resfunc

>>> @decfunc
... def add_ints2(a, b):
...  return a + b * 2
... 

>>> add_ints2(1, 2)
5
```

動作が分かりにくいので、上記のデコレータを変更する。  

```python
>>> def decfunc1(func):
...  def resfunc(*args, **kwargs):
...    print('deffunc1 ')
...    print(args)
...    return [x for x in args if x % 3 == 0]
...  return resfunc
... 

>>> @decfunc1
... def add_ints3(*args):
...  return [x * 2 for x in args]
... 

>>> add_ints3(1,2,3,4,5,6)
deffunc1 
(1, 2, 3, 4, 5, 6)
[3, 6]
```

デコレータは複数持てる。  
`def`のすぐ上から先に実行される。

```python
# -*- coding: utf-8 -*-

def decfunc1(func):
  def resfunc(*args, **kwargs):
    print('deffunc1')
    newarg = func(*args, **kwargs)
    return [x * 2 for x in newarg]
  return resfunc

def decfunc2(func):
  def resfunc(*args, **kwargs):
    print('decfunc2')
    newarg = func(*args, **kwargs)
    return [x for x in newarg if x % 4 == 0]
  return resfunc


@decfunc1
@decfunc2
def add_ints4(*args):
  return [x + 100 for x in args]

print(add_ints4(1,2,3,4,5,6,7,8,9,10))
```

実行結果  

```python
deffunc1
decfunc2
[208, 216]
```

デコレータの順序を前後入れ替えた場合

```python
# 上記コードを修正
@decfunc2
@decfunc1
def add_ints4(*args):
```

```python
decfunc2
deffunc1
[204, 208, 212, 216, 220]
```

コメントは上から順となっているが、`return`する関数の実行順序は下からとなっていることがわかる。

## グローバル変数

global変数を関数内で変更する場合、`global`を使う。  

```python
animal = 'monkey'
def zoo():
  global animal
  animal = 'elephant'
```

## 関数名の取得

現在の関数名は、`関数名.__name__`で取得できる。  
(どういう場面で使うかはわからない)  

```python
def zoo():
  print('this is ' + zoo.__name__)
```
