# defaultdict (from collections)

`defaultdict`というdictのサブクラスがある。  
データをまとめる処理に使えそう。  


```python
from collections import defaultdict

zoo = ['monkey', 'elephant', 'snake', 'rabbit', 'monkey', 'snake']
c = defaultdict(int)
for animal in zoo:
    c[animal] += 1
print(c)

# 実行結果
defaultdict(<class 'int'>, {'snake': 2, 'monkey': 2, 'rabbit': 1, 'elephant': 1})
```

`defaultdict(int)`を`defaultdict(list)`に変更すると、辞書の値が数値からリストに変わる。  


それに伴い、`c[animal] += 1`のところを`append`に変更したコード。  

```python
from collections import defaultdict

zoo = ['monkey', 'elephant', 'snake', 'rabbit', 'monkey', 'snake']
c = defaultdict(list)
for animal in zoo:
    c[animal].append(1)
print(c)

# 実行結果
defaultdict(<class 'list'>, {'snake': [1, 1], 'elephant': [1], 'rabbit': [1], 'monkey': [1, 1]})
```