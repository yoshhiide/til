# Counter

http://docs.python.jp/2/library/collections.html#collections.Counter

`from collections import Counter`

文字列に対して`Counter`を使うと出現文字のカウントを辞書で返す

```python
a = 'aiueojaSAIJFELJJIFJSLAAIJWEKJIUUIUAIU'
Counter(a)
Counter({'J': 6, 'I': 6, 'A': 4, 'U': 4, 'a': 2, 'F': 2, 'L': 2, 'S': 2, 'E': 2, 'e': 1, 'i': 1, 'K': 1, 'j': 1, 'o': 1, 'u': 1, 'W': 1})

Counter(a.lower()).most_common(1)
[('i', 7)]

Counter(a.lower()).most_common(3)
[('i', 7), ('j', 7), ('a', 6)]
```

`most_common()`は上位要素を引数で指定して取得できる