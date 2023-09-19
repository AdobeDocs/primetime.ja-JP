---
title: 使用モデルの実装の概要
description: 使用モデルの実装の概要
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# 使用モデルの実装の概要 {#implementing-the-usage-models-overview}

リファレンス実装には、パッケージ化されたコンテンツの一部に対して次の 4 つの異なる使用モデルを有効にする方法を示すビジネスロジックが含まれています。

* ダウンロード先 (DTO)
* レンタル/ビデオオンデマンド (VOD)
* サブスクリプション（食べ放題）
* 広告が資金を提供する

使用状況モデルのデモを有効にするには、カスタムプロパティを指定します。 `RI_UsageModelDemo=true` パッケージ時に。 Media Packager のコマンドラインツールを使用してコンテンツをパッケージ化する場合は、次のように指定します。

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE]
>
>パッケージ時にオプションのデモモードをアクティベートしない場合、ライセンスサーバーはパッケージ時に指定されたポリシーを使用してライセンスを発行します。 複数のポリシーを指定した場合、ライセンスサーバは最初の有効なポリシーを使用します。

デモでは、サーバー上のビジネスロジックが、生成されたライセンスの実際の属性を制御します。 パッケージ化の際には、最小限のポリシー情報のみをコンテンツに含める必要があります。 特に、ポリシーは、コンテンツへのアクセスに認証が必要かどうかを示すだけで済みます。 4 つの使用モデルをすべて有効にするには、匿名アクセスを許可する 1 つのポリシー（広告資金モデル用）と、ユーザー名/パスワード認証を必要とする 1 つのポリシー（他の 3 つの使用モデル用）を含めます。 ライセンスをリクエストする際、クライアントアプリケーションは、ポリシー内の認証情報に基づいて、ユーザーに認証を求めるかどうかを決定できます。

特定のユーザーがライセンスを発行する使用モデルを制御するために、参照実装データベースにエントリを追加できます。 The `Customer` この表には、ユーザーを認証するためのユーザー名とパスワードが含まれます。 また、ユーザーが購読を持っているかどうかも示します。 サブスクリプションを持つユーザーは、 *購読* 使用モデル。 の下でユーザーにアクセス権を付与するには *ダウンロードして所有* または *ビデオオンデマンド* 使用状況モデルの場合は、 `CustomerAuthorization` テーブル：ユーザーがアクセスできるコンテンツの各部分と使用モデルを指定します。 詳しくは、 [!DNL PopulateSampleDB.sql] 各テーブルへの入力に関する詳細は、スクリプトを参照してください。

ユーザーがライセンスをリクエストすると、参照実装サーバーは、クライアントから送信されたメタデータを調べて、 `RI_UsageModelDemo` プロパティ。 その場合は、次のビジネスルールが使用されます。

* いずれかのポリシーで認証が必要な場合：

   * リクエストに有効な認証トークンが含まれている場合は、顧客データベーステーブルでユーザーを探します。 ユーザーが見つかった場合：

      * 次の場合、 `Customer.IsSubscriber` プロパティは次のとおりです。 `true`、のライセンスを生成 *購読* 使用状況モデルを作成し、ユーザーに送信します。

      * 次の場所でレコードを探します： `CustomerAuthorization` このユーザーおよびコンテンツ ID のデータベーステーブル。 レコードが見つかった場合：

         * 次の場合 `CustomerAuthorization.UsageType` 次に該当 `DTO`、のライセンスを生成 *ダウンロードして所有* 使用状況モデルを作成し、ユーザーに送信します。

         * 次の場合 `CustomerAuthorization.UsageType` 次に該当 `VOD`、のライセンスを生成 *ビデオオンデマンド* 使用状況モデルを作成し、ユーザーに送信します。

   * どのポリシーも匿名アクセスを許可しない場合：

      * リクエストに有効な認証トークンがない場合は、「認証が必要です」というエラーを返します。
      * それ以外の場合は、「許可されていません」エラーが返されます。

* ポリシーの 1 つが匿名アクセスを許可する場合は、広告資金の使用モデルのライセンスを生成し、ユーザーに送信します。

参照実装サーバーが使用モデルデモのライセンスを発行する前に、4 つの使用モデルのそれぞれに対してライセンスの生成方法を指定するようにサーバーを設定する必要があります。 これは、各使用モデルに対してポリシーを指定することでおこなわれます。 リファレンス実装には、4 つのサンプルポリシー ( [!DNL dto-policy.pol], [!DNL vod-policy.pol], [!DNL sub-policy.pol], [!DNL ad-policy.pol]) または独自のポリシーを置き換えることができます。 In [!DNL flashaccess-refimpl.properties]で、次のプロパティを設定して各使用モデルで使用するポリシーを指定し、ポリシーファイルを `config.resourcesDirectory` プロパティ：

```
# Policy file name for Download To Own usage  
RefImpl.UsageModelDemo.Policy.DTO=dto-policy.pol  
# Policy file name for Rental usage  
RefImpl.UsageModelDemo.Policy.VOD=vod-policy.pol  
# Policy file name for Subscription usage  
RefImpl.UsageModelDemo.Policy.Subscribe=sub-policy.pol  
# Policy file name for Ad Supported (free) usage  
RefImpl.UsageModelDemo.Policy.Free=ad-policy.pol
```
