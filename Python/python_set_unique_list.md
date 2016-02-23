# setを使って重複なしのリストを作る
set（集合）型(http://docs.python.jp/2/library/stdtypes.html#set)

Python2.4~

- 一度追加した値と重複する値を追加できない
- setオブジェクトを返す
- 順番なし（保障されない）

```python
>>> s = set()
>>> s.add(1)
>>> s
{1}
>>> s.add(2)
>>> s
{1, 2}
>>> s.add(1)
>>> s
{1, 2}
```

- リストから重複を削除してリスト型にして返す
```python
>>> nouni = [1,2,2,3,2,1]
>>> list(set(nouni))
[1, 2, 3]
```

- リストの順番を変えずに、重複を削除してリスト型にして返す
```python
>>> nouni = [4, 2, 1, 4, 5, 6, 7, 4, 2, 3]
>>> sorted(set(nouni), key = nouni.index)
[4, 2, 1, 5, 6, 7, 3]
```