# with - ファイル自動クローズ


`with`を`open`の前に書くことで、開いたファイルを処理後に自動的にクローズしてくれる。  
  
コードブロックが正常に終了するか、例外生成によって終わると、ファイルは自動的に閉じられる。  
  
ファイルを１行ずつ読み込むコード例  

```python
with open('./opentest/node_merge.txt', 'rt') as nodedoc:
  for line in nodedoc:
    print(line)
```