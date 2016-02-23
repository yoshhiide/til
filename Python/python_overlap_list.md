# リストから重複値のみをリストで返す

listは順番が保障される

```python
>>> nouni = [4, 2, 1, 4, 5, 6, 7, 4, 2, 3]
>>> seen = set()
>>> seen_add = seen.add
>>> list(set([x for x in nouni if x in seen or seen_add(x)]))
[2, 4]
```

順序を変えず(先に出現した順)にリストにする場合は、`sorted`を使う
```python
>>> nouni = [4, 2, 1, 4, 5, 6, 7, 4, 2, 3]
>>> seen = set()
>>> seen_add = seen.add
>>> sorted(list(set([x for x in nouni if x in seen or seen_add(x)])), key = nouni.index)
[4, 2]
```