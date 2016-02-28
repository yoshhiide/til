# 集合(set)

> 集合とは、重複する要素をもたない、順序づけられていない要素の集まりです。 Set オブジェクトは、結合 (union)、交差 (intersection)、差分 (difference)、対称差 (symmetric difference)といった数学的な演算もサポートしています。

http://docs.python.jp/2/tutorial/datastructures.html#sets

## set()
`set()`を使うことで、重複のない集合を作ることができる

```python
>>> a = ['banana', 'banana', 'apple', 'apple']
>>> set(a)
{'banana', 'apple'}
```


## 積集合(&)
両方の集合に含まれているすべての要素を格納する集合

`&`を使うことで積集合を取ることができる

```python
>>> a = {1, 2}
>>> b = {2, 3}
>>> a & b
{2}
```

`intersection()`も同様に積集合となる

```python
a.intersection(b)
```


## 和集合(|)
少なくともどちらかの集合に含まれている要素の集合

`|`を使うことで和集合を取ることができる

```python
>>> a = {1, 2}
>>> b = {2, 3}
>>> a | b
{1, 2, 3}
```

`union()`も同様に和集合となる

```python
a.union(b)
```

## 差集合
第１集合には有るが、第２集合に無いもの  

`-`か`difference()`で差集合を取る  

```python
>>> a = {1, 2}
>>> b = {2, 3}

>>> a - b
{1}
>>> b - a
{3}
>>> a.difference(b)
{1}
```

## 排他的OR(XOR)
どちらか片方にのみ有るもの  

`^`か`symmetric_difference()`で排他的OR(XOR)を取る  

```python
>>> a = {1, 2}
>>> b = {2, 3}

>>> a ^ b
{1, 3}
>>> a.symmetric_difference(b)
{1, 3}
```

## 部分集合
片方の集合がもう一方の部分集合になっているかをBooleanでチェック  

`<=`か`issubset()`

## 真部分集合
`<`

## 上位集合
`>=`か`issuperset()`

## 真上位集合
`>`
