# vue-app


## 概要
 実際に自分の生活にあると便利だと思うものを作りたいと言うことでこのサービスを開発しようと考えました。ジムでトレーニングしている人の中には、ノートとペンでトレーニング記録をつけている人がかなり多いように感じていました。トレーニングをした後のインターバル中で書き込んでいる人が多いのです。インターバル中は息が上がっており、力が入りにくくペンで字を書くことは大変なのではないか、スマートフォンなどのデバイスで簡単に記録できた方が良いのではないかと言う発想からこのアプリケーションを開発しました。
  ※今回作成したものは前回jqueryを用いて作成したアプリケーションをvue.jsで改良したものになります。

## 使用方法
 1.まずグーグルアカウントかメールアドレス・パスワードのどちらかでログインします。
  アカウントがない場合はサインインが必要になります。




 2.ログイン後の画面にあるカレンダーの下についている＋ボタンでその日のトレーニングメニューを記録します。




 3.カレンダーの下にその日の記録を一覧できるテーブルがありそちらで確認ができます
  追加した記録の修正や削除も行えるようになっています。




 4.画面をリロードするとカレンダーのトレーニングした日に印がつきます。




<a href="https://gyazo.com/08246520dab593a2ad2181ff2188de52"><img src="https://i.gyazo.com/08246520dab593a2ad2181ff2188de52.png" alt="Image from Gyazo" width="1353"/></a>






## 使用技術
vue.CLI ver3.9.3

firebase ver9.2.2


## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
