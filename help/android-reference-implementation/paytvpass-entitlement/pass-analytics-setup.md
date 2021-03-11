---
description: リファレンスの実装を設定して、Adobe Analyticsレポートを使用できます。
title: Adobe Analyticsレポートの設定
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Adobe Analyticsレポートの構成{#configure-adobe-analytics-reporting}

リファレンスの実装を設定して、Adobe Analyticsレポートを使用できます。

リファレンスの実装は、Primetime SDKにバンドルされているAdobeモバイルライブラリを使用して、Primetime認証イベントデータをAdobe Analyticsに送信するように設定されています。 アプリから送信されたイベントデータを有効にして使用するには、まずAdobe Analyticsアカウントを作成する必要があります。 アカウントを作成したら、次の操作を行います。

1. アカウント情報を使用してアプリケーションを設定します。と
1. 処理ルールを作成して、レポート内でのイベントデータの表示方法をカスタマイズします。

次の表に、Adobe Analyticsに送信されるデータを示します。

| アクション名 | `a.media.pass.event.MvpdSelection` | ユーザは、選択ダイアログでマルチチャネルビデオプログラミングディストリビタ(MVPD)を選択した |
|---|---|---|
| コンテキストデータ | `a.media.pass.MvpdId (String)` | ユーザーが選択したMVPD |
|  | `a.media.pass.ClientType` | （文字列）「flash」、「html5」、「ios」または「android」のいずれかのクライアントタイプ |
|  |  |  |
| アクション名 | `a.media.pass.event.AuthenticationDetection` | 認証ワークフローが完了しました |
| コンテキストデータ | `a.media.pass.Successful` | （ブール型）トークンリクエストが成功したかどうか、trueまたはfalse |
|  | `a.media.pass.MvpdId` | (String)ユーザーが選択したMVPD |
|  | `a.media.pass.Guid` | (String)追跡ID |
|  | `a.media.pass.Cached` | (Boolean)トークンが既にキャッシュにあります。trueまたはfalse |
|  | `a.media.pass.ClientType` | （文字列）「flash」、「html5」、「ios」または「android」のいずれかのクライアントタイプ |
|  |  |  |
| アクション名 | `a.media.pass.event.AuthorizationDetection` | 承認ワークフローが完了しました |
| コンテキストデータ | `a.media.pass.Successful` | （ブール型）トークンリクエストが成功したかどうか、trueまたはfalse |
|  | `a.media.pass.MvpdId` | (String)ユーザーが選択したMVPD |
|  | `a.media.pass.Guid` | (String)追跡ID |
|  | `a.media.pass.Cached` | (Boolean)トークンが既にキャッシュにあります。trueまたはfalse |
|  | `a.media.pass.Error` | （文字列）認証が失敗した場合のエラー |
|  | `a.media.pass.ErrorDetails` | (String)エラーの詳細 |
|  | `a.media.pass.ClientType` | （文字列）「flash」、「html5」、「ios」または「android」のいずれかのクライアントタイプ |

1. Adobe Marketing Cloudで使用するアプリを設定します。

   Primetime Primetime認証データをAdobe Analyticsに送信できるようにするには、コンパイル時に参照実装に[!DNL `ADBMobileConfig.json`]設定ファイルを追加する必要があります。 これは、Primetime SDKがVideo AnalyticsデータをMarketing Cloudに送信する際に使用する設定ファイルとまったく同じです。 お使いのAdobe Analyticsアカウントでのアプリケーションの設定の詳細については、[Adobe Marketing Cloudのドキュメント](https://microsite.omniture.com/t2/help/en_US/reference/)を参照してください。
1. 処理ルールを作成します。

   リファレンスの実装によって送信されるPrimetime認証イベントデータは、Analyticsレポートに自動的には表示されません。 まず、処理ルールを作成してデータを利用する必要があります。 処理ルール](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html)の作成については、[Adobe Analyticsのドキュメントを参照してください。
