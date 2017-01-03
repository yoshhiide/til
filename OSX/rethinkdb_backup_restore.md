# macOSでインストールしたRethinkDBのbackupとrestore

## インストール

https://www.rethinkdb.com/docs/install/osx/

`brew install rethinkdb`

## バックアップ

> Use the dump subcommand to create an archive of data from the cluster. This creates a tar.gz file consisting of JSON documents and additional table metadata.
  
  
事前にPythonドライバーをインストール  
`sudo pip install rethinkdb`

バックアップ・リストア  
https://rethinkdb.com/docs/backup/  
  
`rethinkdb dump`  

host,port指定  
`rethinkdb dump -c localhost:28015`  

file指定  
`rethinkdb dump -f rethinkdb_dump/backup-0101.tar.gz`

## リストア

`rethinkdb restore rethinkdb_dump/backup-0101.tar.gz`  
  
  
host,port指定  
`rethinkdb restore backup.tar.gz -c localhost:28015`  
  
**既存DB,tableに上書きする為には、`--force`オプションが必要**  
`rethinkdb restore backup.tar.gz --force`