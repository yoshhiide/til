# enumerate

遅延評価ジェネレータでイテレータをラップする。  
ループの添字とイテレータの値をyieldする。  

```python
>>> animals = ['monkey', 'tiger', 'elephant', 'hipopo']

>>> [zoo for zoo in animals]
['monkey', 'tiger', 'elephant', 'hipopo']

>>> [(i, zoo) for i, zoo in enumerate(animals)]
[(0, 'monkey'), (1, 'tiger'), (2, 'elephant'), (3, 'hipopo')]

>>> {i: zoo for i, zoo in enumerate(animals)}
{0: 'monkey', 1: 'tiger', 2: 'elephant', 3: 'hipopo'}

>>> {i: zoo for i, zoo in enumerate(animals, 1)}
{1: 'monkey', 2: 'tiger', 3: 'elephant', 4: 'hipopo'}
```