---
description: Adobe Analyticsレポートを使用するようにリファレンスの実装を設定できます。
seo-description: Adobe Analyticsレポートを使用するようにリファレンスの実装を設定できます。
seo-title: Adobe Analyticsレポートの設定
title: Adobe Analyticsレポートの設定
uuid: bdf8bb7f-a0c8-48a2-a632-0b872687f3fe
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# Adobe Analyticsレポートの設定 {#configure-adobe-analytics-reporting}

Adobe Analyticsレポートを使用するようにリファレンスの実装を設定できます。

リファレンスの実装は、Primetime SDKにバンドルされたAdobe Mobile Libraryを使用して、Primetime認証イベントデータをAdobe Analyticsに送信するように設定されます。 アプリケーションから送信されたイベントデータを有効にして使用するには、まずAdobe Analyticsアカウントを作成する必要があります。 アカウントの作成後：

1. アカウント情報を使用してアプリケーションを設定します。および
1. 処理ルールを作成して、レポート内でのイベントデータの表示方法をカスタマイズします。

次の表に、Adobe Analyticsに送信されるデータを示します。

| アクション名 | `a.media.pass.event.MvpdSelection` | ユーザは、選択ダイアログでマルチチャネルビデオプログラミングディストリビタ(MVPD)を選択した |
|---|---|---|
| コンテキストデータ | `a.media.pass.MvpdId (String)` | ユーザが選択したMVPD |
|  | `a.media.pass.ClientType` | （文字列）クライアントのタイプを「flash」、「html5」、「ios」または「android」にします。 |
|  |  |  |
| アクション名 | `a.media.pass.event.AuthenticationDetection` | 認証ワークフローが完了しました |
| コンテキストデータ | `a.media.pass.Successful` | （ブール型）トークンリクエストが成功したか、trueまたはfalse |
|  | `a.media.pass.MvpdId` | （文字列）ユーザーが選択したMVPD |
|  | `a.media.pass.Guid` | （文字列）追跡ID |
|  | `a.media.pass.Cached` | (Boolean)トークンは既にキャッシュに存在します。trueまたはfalse |
|  | `a.media.pass.ClientType` | （文字列）クライアントのタイプを「flash」、「html5」、「ios」または「android」にします。 |
|  |  |  |
| アクション名 | `a.media.pass.event.AuthorizationDetection` | 承認ワークフローが完了しました |
| コンテキストデータ | `a.media.pass.Successful` | （ブール型）トークンリクエストが成功したか、trueまたはfalse |
|  | `a.media.pass.MvpdId` | （文字列）ユーザーがMVPDを選択した場合 |
|  | `a.media.pass.Guid` | （文字列）追跡ID |
|  | `a.media.pass.Cached` | (Boolean)トークンは既にキャッシュに存在します。trueまたはfalse |
|  | `a.media.pass.Error` | （文字列）認証に失敗した場合のエラー |
|  | `a.media.pass.ErrorDetails` | （文字列）エラーの詳細 |
|  | `a.media.pass.ClientType` | （文字列）クライアントのタイプを「flash」、「html5」、「ios」または「android」にします。 |

1. Adobe Marketing Cloudで使用するアプリを設定します。

   Primetime Primetime認証データをAdobe Analyticsに送信できるようにするには、コンパイル時に [!DNL `ADBMobileConfig.json`] 設定ファイルを参照実装に追加する必要があります。 これは、Primetime SDKがVideo AnalyticsデータをMarketing Cloudに送信する際に使用する設定ファイルとまったく同じです。 Adobe Analyticsアカウントでのアプリケ [ーションの設定について詳しくは](https://microsite.omniture.com/t2/help/en_US/reference/) 、Adobe Marketing Cloudのドキュメントを参照してください。
1. 処理ルールを作成します。

   リファレンスの実装によって送信されるPrimetime認証イベントデータは、Analyticsレポートに自動的には表示されません。 まず、処理ルールを作成してデータを利用する必要があります。 処理ルールの作成につい [ては、Adobe Analyticsのドキュメントを参照してください](https://microsite.omniture.com/t2/help/en_US/reference/processing_rules.html)。
