# 内包表記

mapやfilterの代わりに使うと高速化につながるらしい内包表記は、リストのみならず辞書や集合を作ることもできる。

辞書の場合

```python
>>> word = 'letters'
>>> {letter: word.count(letter) for letter in set(word)}
{'e': 2, 't': 2, 's': 1, 'l': 1, 'r': 1}
```

集合の場合

```python
>>> {x for x in range(6) if x % 2 == 0}
{0, 2, 4}
```

ジェネレータ内包表記  
内包表記にはタプルがない。`()`とするとジェネレータ内包表記となる。  
ジェネレータは一度しか実行できない。  

```python
>>> gen = (x for x in range(6) if x % 2 == 0)
>>> [x for x in gen]
[0, 2, 4]

# 二度目は何も出てこない
>>> [x for x in gen]
[]

>>> print(gen)
<generator object <genexpr> at 0x1054881f8>
```