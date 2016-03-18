# Node.js ディレクトリ有無を確認＆なければ作成

`fs.exists`や`path.exists`(syncも)はdeprecatedなので、別の方法で存在確認を行う。  

```js
const statMkdirDirectory = (Path) => {
  return new Promise((resolve, reject) => {
    fs.stat(Path, (err, stat) => {
      if (err) {
        // Dir not exists -> create dir
        fs.mkdirAsync(Path)
          .then(()     => resolve(true))
          .catch((err) => reject(err));
        return;
      }
      // Dir exists
      resolve(true);
    });
  });
};

const mkdirAsync = (Path) => {
  return new Promise((resolve, reject) => {
    fs.mkdir(Path, (err) => {
      if (err) {
        return reject(false);
      }
      resolve(true);
    })
  });
};
```

ディレクトリの確認せずに、最初から`mkdir`するなら`reject -> resolve`

```js
const mkdirAsync = (Path) => {
  return new Promise((resolve, reject) => {
    fs.mkdir(Path, (err) => {
      if (err) {
        return resolve(false);
      }
      resolve(true);
    })
  });
};
```
