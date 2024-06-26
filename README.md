# Howto make Web API using Azure LogicApps
このサンプルは Azure Logic Apps を使用して Web API ライクなアプリケーションを作成するための手順について紹介します。

## はじめに

Microsoft Azure はホストするアプリケーションの形態に応じて、さまざまなサービスを提供しています。たとえば、Web API サービスのホストには、基本となる [Azure App Service](https://learn.microsoft.com/ja-jp/azure/app-service/overview) はもちろん、関数型の API をサーバーレス環境でホストできる [Azure Functions](https://learn.microsoft.com/ja-jp/azure/azure-functions/functions-overview?pivots=programming-language-javascript) がありますが、[Azure Logic Apps](https://learn.microsoft.com/ja-jp/azure/logic-apps/logic-apps-overview) でも Web API のようなサービスを提供することができます。

### Azure Logic Apps とは

Logic Apps はビジュアルデザインツールを使用してノーコードでワークフローを記述するものです。

ワークフローはトリガー、コネクタ、アクションでという要素を組み合わせて記述していきますが、特徴的なのはどれも外部サービスとの連携がシームレスに行えるということです。

たとえば、RSS トリガーを使って、外部の Web コンテンツの更新を監視し、更新されたら更新情報を受け取り、Teams の任意のチャネルに投稿を行う、といったことがノーコードで記述できます。

トリガーやコネクターやアクションは多くの外部サービスに対応しており、それら外部サービスの機能を利用するのにわざわざ API を調べて個別にコーティングを行う必要はなく、一つのワークフローの中で複数の外部サービスの機能を利用する場合でも、面倒な同期処理を記述する必要はありません。また、ワークフローの内容が変更になった際も、ビジュアルデザイナーで UI を操作するだけでよくわざわざコーティングをし直す必要はありません。

こうしたワークフローのシナリオに合致するものであれば、Logic Apps を使用することで開発のスピードをあげメンテナンスコストを下げることができます。

Azure Logic Apps は Request トリガーと Response アクションを組み合わせて REST API として利用することがですます。つまり、コーティングスキルのない人でも入力と出力のルールさえ理解してしまえば REST API が書けるということになります。

## 要件

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

このふたつのサービスの違いについては以下のドキュメントを参照してください。

* [Standard シングルテナント ロジック アプリと従量課金マルチテナント ロジック アプリの違い](https://learn.microsoft.com/ja-jp/azure/logic-apps/single-tenant-overview-compare)

## 目次

1. [**JSON データに応答を返すLogic Apps の作成**](ex01.md)
2. [**作成した Logic Apps の検証**](ex02.md)
3. [**まとめ**](ex03.md)

---
## LICENSE

このドキュメントに記載されている情報 (URL や他のインターネット Web サイト参照を含む) は、将来予告なしに変更することがあります。別途記載されていない場合、このソフトウェアおよび関連するドキュメントで使用している会社、組織、製品、ドメイン名、電子メール アドレス、ロゴ、人物、場所、出来事などの名称は架空のものです。実在する商品名、団体名、個人名などとは一切関係ありません。お客様ご自身の責任において、適用されるすべての著作権関連法規に従ったご使用をお願いいたします。

マイクロソフトは、このドキュメントに記載されている内容に関し、特許、特許申請、商標、著作権、またはその他の無体財産権を有する場合があります。別途マイクロソフトのライセンス契約上に明示の規定のない限り、このドキュメントはこれらの特許、商標、著作権、またはその他の知的財産権に関する権利をお客様に許諾するものではありません。

製造元名、製品名、URL は、情報提供のみを目的としており、これらの製造元またはマイクロソフトのテクノロジを搭載した製品の使用について、マイクロソフトは、明示的、黙示的、または法令によるいかなる表明も保証もいたしません。製造元または製品に対する言及は、マイクロソフトが当該製造元または製品を推奨していることを示唆するものではありません。掲載されているリンクは、外部サイトへのものである場合があります。これらのサイトはマイクロソフトの管理下にあるものではなく、リンク先のサイトのコンテンツ、リンク先のサイトに含まれているリンク、または当該サイトの変更や更新について、マイクロソフトは一切責任を負いません。リンク先のサイトから受信した Web キャストまたはその他の形式での通信について、マイクロソフトは責任を負いません。マイクロソフトは受講者の便宜を図る目的でのみ、これらのリンクを提供します。また、リンクの掲載は、マイクロソフトが当該サイトまたは当該サイトに掲載されている製品を推奨していることを示唆するものではありません。

Copyright (c) Microsoft Corporation. All rights reserved.



