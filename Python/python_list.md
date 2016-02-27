# list

リストは要素の順番を管理、内容変更できる。

辞書や集合は`list()`でリストにすることができる。

```python
>>> d = {'red':'stop', 'yellow':'go fast'}
>>> list(d)
['red', 'yellow']

>>> d = {'red':'stop', 'yellow':'go fast'}
>>> list(set(d))
['red', 'yellow']
```

`zip()`で複数のリストを並列的に処理できる。

```python
>> a = [1,2,3,4,5]
>>> b = [10, 20, 30, 40]
>>> c = [100, 200, 300, 400]
>>> [x+y+z for x, y, z in zip(a, b, c)]
[111, 222, 333, 444]
```