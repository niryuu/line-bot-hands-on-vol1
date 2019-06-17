# 第1部 オウム返しBot の開発

## ディレクトリ作成＆ソースコード クローン

```bash
$ mkdir ~/ldgk-hands-on && cd ~/ldgk-hands-on
$ git clone https://github.com/sumihiro3/line-bot-hands-on-vol1.git
$ cd line-bot-hands-on-vol1
```

## プログラムに必要なモジュールをインストール

```bash
$ npm install
```

## ngrok インストール＆起動

```bash
$ npm install -g ngrok

$ ngrok http 3000
```

## LINE Bot の設定

### 下記資料を参照

https://******** 

### 環境変数を設定

.env ファイルを編集

```text
CHANNEL_ACCESS_TOKEN="XXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
CHANNEL_SECRET="XXXXXXXXXXXX"
BASE_URL="https://XXXXXX.ngrok.io"
```

## プログラムの起動

```bash
$ node index.js
```

# 第2部 クイズBot の開発

## リッチメニューの設定

### 下記資料を参照

https://******** 

## プログラムの起動

```bash
$ node app.js
```

## FlexMessage を使ったメッセージを送ってみよう

### 全問回答後のメッセージをFlexMessage 化する

```javascript:app.js 172 行目付近
// 前略
} else if (postback_type === POSTBACK_TYPE_SHOW_QUIZ_RESULT) {
        // クイズの結果を見る
        const quiz_result = quiz.getQuizeResultFor(user_id);
        let message = {};
        if (quiz_result != null) {
            // TODO クイズの結果をFlexMessage で返す
            message = {'type': 'text', 'text': quiz_result['message']};
        } else {
            // 回答が終わっていなかった場合
            message = generateInvalidOperationMessage();
        }
        return client.replyMessage(replyToken, message);
} else {
// 後略
```
