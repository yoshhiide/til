# dict

python3~を例とする

辞書(dict)はリストと異なり、順序が管理されていない。  
つまり、順番はない。  


```python
d = {'green': 'go', 'yellow': 'fast', 'red': 'stop'}
```

[] - 要素の追加・変更

```python
d['white'] = 'watch out'
d
{'white': 'watch out', 'red': 'stop', 'yellow': 'fast', 'green': 'go'}

d['green']
'go'
```

update() - 結合

```python
e = {'black': 'light', 'blue': 'equal green'}

d.update(e)
d
{'black': 'light', 'red': 'stop', 'green': 'go', 'white': 'watch out', 'yellow': 'fast', 'blue': 'equal green'}
```

del - 削除

```python
del d['black']
d
{'red': 'stop', 'green': 'go', 'white': 'watch out', 'yellow': 'fast', 'blue': 'equal green'}

del d['black']
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
KeyError: 'black'
```

clear() - 全削除

```python
d.clear()
d
{}
```

```python
d = {}
d
{}
```

要素の取得

[], in, get()

```python
d['green']

'green' in d

d.get('green')
```

get()について便利な使い方ができる

```python
d.get('skyblue')
<何も出ない>


if d.get('greenn'):
    print(True)
else:
    print(False)

False
```

```python
d.get('greenn', 'not a python')

'not a python'
```

keys() - キー取得

リテラブルなdict_keysである為、リスト利用する場合には、
python3~では、list()で包む必要がある。

```python
d.keys()
dict_keys(['white', 'red', 'yellow', 'green', 'blue'])

list(d.keys())
['white', 'red', 'yellow', 'green', 'blue']
```

values() - 値の取得

```python
list(d.values())
['watch out', 'stop', 'fast', 'go', 'equal green']
```

items() - key/valueの取得

```python
list(d.items())
[('white', 'watch out'), ('red', 'stop'), ('yellow', 'fast'), ('green', 'go'), ('blue', 'equal green')]


>>> for x, y in d.items():
...   print(x, y)
white watch out
red stop
yellow fast
green go
blue equal green
```

copy() - コピー

```python
# 参照を避ける
dc = d.copy()
```
