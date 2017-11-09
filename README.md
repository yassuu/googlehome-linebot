googlehome-linebot
====

google-homeがLINE-BOTの音声インターフェースとなって、LINEを持っていない子供とのコミュニケーションを可能とします

## Requirement
googlehome-linebot requires the following to run:

  * [Node.js][node] 8.0+
  * [npm][npm] (normally comes with Node.js)
  * [google-home-notifier]
  * [line-bot-sdk-nodejs]
  * [firebase-admin]

## Usage

事前に以下サービスへの登録が必要となります。
- (必須)LINE Messaging API
  - LINE BOT本体
- (必須)IFTTT
  - google homeと連携し、firebase(webhook)経由で **googlehome-linebot** を呼ぶ出します
- (必須)Dialogflow
  - LINEBOTと連携
- (任意)Cloud Function
  - DialogflowからLINEの内容をfirebaseに書込むために使用します
  - Dialogflowから直接 **googlehome-linebot** をwebhookで呼び出す場合は不要です
- (任意)firebase
  - 更新時の通知を利用して、**googlehome-linebot** の機能を呼び出すために使用します
  - **googlehome-linebot** をwebhookで呼び出す場合は不要です

各サービスのフローは以下の通りです。(firebase経由の場合)
- ###### LINE-BOTからgooglehomeへのメッセージ送信
  - [LINE会話] -> [linebot] -> [dialogflow] -> [cloud function] -> [firebase] -> **[googlehome-linebot]** -> [googlehome]
- ###### googlehomeからLINE-BOTへのメッセージ送信
  - [googlehome] -> [ifttt] -> [firebase] -> **[googlehome-linebot]** -> [linebot] -> [LINE会話]
- ###### googlehomeからLINEメッセージの読み上げ
  - [googlehome] -> [ifttt] -> [firebase] -> **[googlehome-linebot]** -> [googlehome]

詳細のサービス連携の使用方法は以下を参照してください。

[TBA]

## Install
事前に以下のインストールが必要
* [google-home-notifier]
* [line-bot-sdk-nodejs]
* [firebase-admin]

```sh
$ npm install
```


[node]: https://nodejs.org/
[npm]: https://www.npmjs.com/
[google-home-notifier]: https://github.com/noelportugal/google-home-notifier
[line-bot-sdk-nodejs]: https://github.com/line/line-bot-sdk-nodejs
[firebase-admin]: https://github.com/firebase/firebase-admin-node
