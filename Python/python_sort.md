# sort

python3~  

pythonには`list.sort`と`sorted`がある。  
`list.sort`はリストをソートする。  
`sorted`はイテラブルをソートできる。  


単純なソート（昇順、降順）

```python
>>> zoo = ['monkey', 'snake', 'elephant', 'hipopo']

>>> sorted(zoo)
['elephant', 'hipopo', 'monkey', 'snake']

>>> sorted(zoo, reverse=True)
['snake', 'monkey', 'hipopo', 'elephant']
```

要素内の対象を指定したソート

```python
>>> animals = [('monkey', 10), ('snake', 40), ('elephant', 20), ('hipopo', 30)]

>>> sorted(animals, key=lambda animal: animal[1])
[('monkey', 10), ('elephant', 20), ('hipopo', 30), ('snake', 40)]
```

さらに高速にする為に、`operator`モジュールを使う

`from operator import itemgetter, attrgetter`

ラムダ式を書かなくても良くなった。

```python
>>> from operator import itemgetter, attrgetter

>>> sorted(animals, key=itemgetter(1))
[('monkey', 10), ('elephant', 20), ('hipopo', 30), ('snake', 40)]
```

他にも、ソート対象を複数指定することもできる。

```python
>>> sorted(animals, key=itemgetter(1,0), reverse=True)
[('snake', 40), ('hipopo', 30), ('elephant', 20), ('monkey', 10)]
```

同じキーがある場合、ソートは元々の順序が維持される。

```python
>>> animals = [('monkey', 50), ('monkey', 40), ('elephant', 20), ('hipopo', 30)]

>>> sorted(animals, key=itemgetter(0))
[('elephant', 20), ('hipopo', 30), ('monkey', 50), ('monkey', 40)]

>>> sorted(animals, key=lambda animal: animal[0])
[('elephant', 20), ('hipopo', 30), ('monkey', 50), ('monkey', 40)]
```