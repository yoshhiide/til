# 関数のキーワード専用引数

python3~
(python2では不可)

関数を呼び出す際に、キーワード付き引数を強制することができる。  
(キーワード付きでない場合にエラーを出す)  


```python
def zoo(animal, kind, *, name, age):
  print(animal)

# error
>>> zoo('monkey', 'honyurui', 'montaro', 4)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: zoo() takes 2 positional arguments but 4 were given

# ok!
>>> zoo('monkey', 'honyurui', name='montaro', age=4)
monkey
```