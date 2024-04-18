# Howto make Web API using Azure LogicApps
Azure Logic Apps を使用して Web API ライクなアプリケーションを作成するための手順について紹介します。

この手順を実行するのに必要となるものは以下です。

- [Microsoft Azure アカウント](https://azure.microsoft.com/ja-jp/free/)
    - Logic Apps 作成権限
- [Outlook.com](Outlook.com) のメール アカウント (無料で作成できます) 
- [Visual Studio Code](https://code.visualstudio.com/Download) 
(検証に使用)
    - [REST Client 拡張](https://marketplace.visualstudio.com/items?itemName=humao.rest-client)


## 作成する Logic Apps の概要

クライアントから HTTP POST メソッドで送信された JSON データを解析し、その内容をメールとして送信、同時に受信したデータを JSON としてレスポンスする Logic Apps を作成します。

なお、この手順で使用する Azure Logic Apps は従量課金のものを使用します。Standard を利用されている方は UI を適宜読み替えてください。

なお、このふたつのサービスの違いについては以下のドキュメントを参照してください。

* [**Standard シングルテナント ロジック アプリと従量課金マルチテナント ロジック アプリの違い**](https://learn.microsoft.com/ja-jp/azure/logic-apps/single-tenant-overview-compare)

## 目次

1. [JSON データに応答を返すLogic Apps の作成](#ex01.md)
2. [作成した Logic Apps の検証](#ex02.md)



