# リストとタプルのメモリ領域確保と処理速度

### list
listはそのサイズによってメモリ上に余剰な領域を確保する。  
appendしていき、サイズが領域を確保する計算式で求めるサイズになると、リストをコピーして新たな余剰領域があるリストをつくる。  

リストを作る -> その分のサイズ＋余剰分(計算式に基づく)のメモリ領域を確保  

### tuple
タプルはそのサイズ分しかメモリ確保しない。  
タプル同士の結合では、新しくメモリ確保することになる。
  
  
### 処理速度
リストは使われなくなった変数のメモリを解放し、osに返すが、タプルは1〜20の小さい場合はOSに返さないで次に同じサイズのタプルが必要になったときに使われる。  
これによってOSとのやりとりを回避している。  
リストとタプルの生成時間の差は**5.1倍**にもなる。