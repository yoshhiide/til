# MacにPython(pyenv)インストール

MacBook(el capitan)


### pyenvのインストール
`brew install pyenv`

- パスを通す  
`dotfiles/.bash_profile`  
下記追加  
`if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi`


### virtualenvのインストール
pip install virtualenv

- pythonの開発慣例
↓virtualenvを使って、プロジェクトごとにインストールするのが適切

### zlibインストール(pyenv 実行に必要)

- 下記より手動ダウンロード  
https://sourceforge.net/projects/libpng/files/zlib/
  
移動させて解凍    
`~/src/`  
  
解凍したディレクトリに入ってコマンド  
```
./configure
make
sudo make install
```

### pyenv実行  
`pyenv install 3.4.2`  
`pyenv install 2.7.9`  

- 切り替え(pyenv global / pyenv rehash)  
```
pyenv global 3.4.2
pyenv rehash
```

- ローカルディレクトリのみ切り替え(pyenv local)  
`pyenv local 3.4.2`


- 確認  
```
pyenv versions
python --version
```

### pipインストール(pyenvでインストールしたpythonについてくる)  
`easy_install pip`

- グローバルインストール  
`pip install [パッケージ名]`  

- ローカルインストール（ユーザーディレクトリにインストール）  
`pip install --user [パッケージ名]`

- インストールしたパッケージ名表示  
`pip freeze`


### virtualenv実行（仮想環境の作成）
```sh
# 作成
virtualenv dev1

# アタッチ（有効化）
source dev1/bin/activate

# デタッチ（無効化）
source deactivate
```


### （pipもローカルでのインストールとみなされる）
```
pip install xxx
python ppp.py
```