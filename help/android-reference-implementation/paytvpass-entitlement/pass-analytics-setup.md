---
description: Adobe Analyticsレポートを使用するように参照実装を設定できます。
title: Adobe Analytics Reporting の設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Adobe Analytics Reporting の設定 {#configure-adobe-analytics-reporting}

Adobe Analyticsレポートを使用するように参照実装を設定できます。

参照実装は、Primetime SDK にバンドルされているAdobeモバイルライブラリを使用して、Primetime 認証イベントデータをAdobe Analyticsに送信するように設定されます。 アプリケーションから送信されたイベントデータを有効にして使用するには、まずAdobe Analyticsアカウントを作成する必要があります。 アカウントを作成したら、次の手順に従います。

1. アカウント情報を使用してアプリケーションを設定し、
1. 処理ルールを作成して、レポート内でのイベントデータの表示方法をカスタマイズします。

次の表に、Adobe Analyticsに送信されるデータを示します。

| アクション名 | `a.media.pass.event.MvpdSelection` | ユーザは、選択ダイアログでマルチチャネルビデオプログラミングディストリバクタ (MVPD) を選択しました。 |
|---|---|---|
| コンテキストデータ | `a.media.pass.MvpdId (String)` | ユーザーが選択した MVPD |
|  | `a.media.pass.ClientType` | (String) クライアントのタイプは、「flash」、「html5」、「ios」または「android」です。 |
|  | | |
| アクション名 | `a.media.pass.event.AuthenticationDetection` | 認証ワークフローが完了しました |
| コンテキストデータ | `a.media.pass.Successful` | (Boolean) トークンリクエストが成功したか、true か、false か |
|  | `a.media.pass.MvpdId` | (String) ユーザーが選択した MVPD |
|  | `a.media.pass.Guid` | (String) トラッキング ID |
|  | `a.media.pass.Cached` | (Boolean) トークンは既にキャッシュに存在します（true または false）。 |
|  | `a.media.pass.ClientType` | (String) クライアントのタイプは、「flash」、「html5」、「ios」または「android」です。 |
|  | | |
| アクション名 | `a.media.pass.event.AuthorizationDetection` | 認証ワークフローが完了しました |
| コンテキストデータ | `a.media.pass.Successful` | (Boolean) トークンリクエストが成功したか、true か、false か |
|  | `a.media.pass.MvpdId` | (String) ユーザーが選択した MVPD |
|  | `a.media.pass.Guid` | (String) トラッキング ID |
|  | `a.media.pass.Cached` | (Boolean) トークンは既にキャッシュに存在します（true または false）。 |
|  | `a.media.pass.Error` | (String) 認証が失敗した場合のエラー。 |
|  | `a.media.pass.ErrorDetails` | (String) その他のエラーの詳細 |
|  | `a.media.pass.ClientType` | (String) クライアントのタイプは、「flash」、「html5」、「ios」または「android」です。 |

1. アプリケーションをAdobe Marketing Cloudで使用するように設定します。

   Primetime Primetime 認証データをAdobe Analyticsに送信する方法 ( [!DNL `ADBMobileConfig.json`] コンパイル時に、参照実装に設定ファイルを追加する必要があります。 これは、Video Analytics データをMarketing Cloudに送信するために Primetime SDK で使用される設定ファイルとまったく同じです。 詳しくは、 [Adobe Marketing Cloudドキュメント](https://microsite.omniture.com/t2/help/en_US/reference/) を参照してください。
1. 処理ルールを作成します。

   参照実装によって送信された Primetime 認証イベントデータは、Analytics レポートに自動的には表示されません。 まず、処理ルールを作成して、データを使用する必要があります。 詳しくは、 [Adobe Analyticsの処理ルール作成に関するドキュメント](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html).
