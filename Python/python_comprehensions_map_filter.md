# mapやfilterを内包表記で書く
http://www.secnetix.de/olli/Python/list_comprehensions.hawk

- 内包表記で書くと高速化につながるらしい  
- map, filterと同等のことができる  
  
#### mapと同等の処理を内包表記で
```python
# リストの値をそれぞれ10倍にしてリストで返す
>>> items = [1,2,3,4,5]
>>> [x*10 for x in items]
[10, 20, 30, 40, 50]
```

#### filterと同等の処理を内包表記で
```python
# リストから2の剰余が0となる値だけをリストで返す
>>> items = [1,2,3,4,5]
>>> [x for x in items if x % 2 == 0]
[2, 4]
```

#### その他、組み合わせ

- 0~9の値から2の剰余が0となる値をリストで返す  
```python
>>> [x for x in range(10) if x % 2 == 0]
[0, 2, 4, 6, 8]
```

- リストの順序を変えずに重複値をユニークにしてリストで返す  
http://stackoverflow.com/questions/480214/how-do-you-remove-duplicates-from-a-list-in-python-whilst-preserving-order
```python
>>> nouni = [4,2,1,4,5,6,7,4,2,3]
>>> seen = set()
>>> seen_add = seen.add
>>> [x for x in nouni if not (x in seen or seen_add(x))]
[4, 2, 1, 5, 6, 7, 3]
```

どちらが効率が良いかはわからないけど
> python_set_unique_list.md

- リストの順番を変えずに、重複を削除してリスト型にして返す
```python
>>> nouni = [4, 2, 1, 4, 5, 6, 7, 4, 2, 3]
>>> sorted(set(nouni), key = nouni.index)
[4, 2, 1, 5, 6, 7, 3]
```
