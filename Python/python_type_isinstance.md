# オブジェクトの型を判定する

python2.2~

型を出力するには、`type`を、  
型を判定するには、`isinstance`を使う。  


- type  
```python
>>> type(1)
<class 'int'>

>>> type('1')
<class 'str'>

>>> type([])
<class 'list'>

>>> type({})
<class 'dict'>

>>> type(())
<class 'tuple'>
```

- isinstance  
```python
>>> isinstance(1, int)
True

>>> isinstance('1', str)
True

>>> isinstance([], list)
True

>>> isinstance({}, dict)
True

>>> isinstance((), tuple)
True
```