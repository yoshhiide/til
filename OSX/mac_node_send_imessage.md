# MacでNode.jsを使ってiMessageを送信する

MacでNode.jsを実行するのであれば、NPMモジュールを使って簡単にiMessageを送信できた。  

会社から帰る際の「今から帰ります。」メールを送信する手間が省ける可能性がある。  
例えば、なんらかのスイッチを押すだけで実行できるようにするとか、指定時間後に会社から離れると実行するとか、トリガーは別に用意すればなんとかなりそう。  


### 環境
OSX 10.11.3  
Node.js v5.7.1

### 使ったモジュール

[osa-imessage https://www.npmjs.com/package/osa-imessage](https://www.npmjs.com/package/osa-imessage)

`npm install --save osa-imessage`

### 送信先について
相手のicloudアカウントか日本なら`+81`から始める電話番号、連絡帳登録している名前を指定して送信する。  
試してみたところ、icloudでしか送信できなかった。  
`.getContact`を使えばできるのかもしれない。

### 送信元について
MacのiMessageに登録している自分のアカウントから送信される。  
下記コードで送信すると、iMessageがバックグラウンドで起動する。  

### コード

```js
'use strict';
const messages = require('osa-imessage');

messages.send('今から帰ります。ご飯の用意を1時間30分後にお願いします。', '<相手のicloudアカウントor電話番号>', () => {
  console.log('送信開始した。');
});
```
