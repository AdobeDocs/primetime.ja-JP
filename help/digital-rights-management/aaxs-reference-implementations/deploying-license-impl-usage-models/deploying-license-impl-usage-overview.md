---
seo-title: 使用モデルの実装の概要
title: 使用モデルの実装の概要
uuid: 1041bb84-9996-4284-b2a0-d6fc6d4b73d9
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---


# 使用モデルの実装の概要 {#implementing-the-usage-models-overview}

リファレンスの実装には、パッケージ化されたコンテンツの1つに対して次の4つの異なる使用モデルを有効にする方法を示すビジネスロジックが含まれています。

* ダウンロードして所有(DTO)
* レンタル/ビデオオンデマンド(VOD)
* 購読
* 広告出資の

使用モデルのデモを有効にするには、パッケージ化の際にカスタムプロパティ `RI_UsageModelDemo=true` を指定します。 Media Packagerコマンドラインツールを使用してコンテンツをパッケージ化する場合は、次のように指定します。

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE]
>
>パッケージ化の際にオプションのデモモードをアクティブにしない場合、ライセンスサーバーはパッケージ化の際に指定されたポリシーを使用してライセンスを発行します。 複数のポリシーを指定した場合、ライセンスサーバーは最初の有効なポリシーを使用します。

デモでは、サーバーのビジネスロジックが生成されるライセンスの実際の属性を制御します。 パッケージ化の際には、最小限のポリシー情報のみをコンテンツに含める必要があります。 特に、ポリシーは、コンテンツへのアクセスに認証が必要かどうかを示すだけで済みます。 4つの使用モデルすべてを有効にするには、匿名アクセスを許可する1つのポリシー（広告提供モデル用）と、ユーザー名/パスワード認証を必要とする1つのポリシー（他の3つの使用モデル用）を含めます。 ライセンスを要求する場合、クライアントアプリケーションは、ポリシーの認証情報に基づいて、ユーザーに認証を求めるかどうかを決定できます。

ライセンスを発行する特定のユーザの使用モデルを制御するために、参照実装データベースにエントリを追加できます。 この `Customer` 表には、ユーザーを認証するためのユーザー名とパスワードが含まれています。 また、ユーザーに購読があるかどうかも示します。 購読を持つユーザーは、 *購読* 使用モデルの下でライセンスが発行されます。 「 *Download to Own* (所有者への *ダウンロード)* 」または「 `CustomerAuthorization` Video on Demand（ビデオオンデマンド）」の使用モデルでユーザーアクセスを許可するために、エントリをテーブルに追加し、ユーザーがアクセスできるコンテンツの各部分と使用モデルを指定できます。 各テーブルの入力について詳しくは、 [!DNL PopulateSampleDB.sql] スクリプトを参照してください。

ユーザーがライセンスを要求すると、参照実装サーバーは、クライアントから送信されたメタデータを調べて、コンテンツが `RI_UsageModelDemo` プロパティを使用してパッケージ化されたかどうかを判断します。 その場合は、次のビジネスルールが使用されます。

* いずれかのポリシーで認証が必要な場合：

   * リクエストに有効な認証トークンが含まれている場合は、Customerデータベーステーブルでユーザーを探します。 ユーザーが見つかった場合：

      * プ `Customer.IsSubscriber` ロパティが `true`の場合は、 *購読* 使用モデルのライセンスを生成し、ユーザに送信します。

      * このユーザーとコンテンツIDのレコードを `CustomerAuthorization` データベーステーブルで検索します。 レコードが見つかった場合：

         * が選択さ `CustomerAuthorization.UsageType` れている場合は、「Download To Own `DTO`** 」使用モデルのライセンスを生成し、ユーザに送信します。

         * が含ま `CustomerAuthorization.UsageType` れている場合は、 `VOD`Video On Demand ** 使用モデルのライセンスを生成し、ユーザに送信します。
   * 匿名アクセスを許可するポリシーがいずれもない場合：

      * 要求内に有効な認証トークンがない場合は、「認証が必要です」というエラーを返します。
      * それ以外の場合は、「認証されていません」というエラーが返されます。


* 匿名アクセスを許可するポリシーの1つがある場合は、広告が出資する使用モデルのライセンスを生成し、ユーザーに送信します。

参照実装サーバーが使用モデルのデモのライセンスを発行する前に、4つの使用モデルのそれぞれに対してライセンスを生成する方法を指定するようにサーバーを設定する必要があります。 これは、各使用モデルにポリシーを指定することで行われます。 リファレンスの実装には、4つのサンプルポリシー( [!DNL dto-policy.pol]、、、 [!DNL vod-policy.pol][!DNL sub-policy.pol]、 [!DNL ad-policy.pol])が含まれています。また、独自のポリシーを置き換えることもできます。 で、次のプロパティ [!DNL flashaccess-refimpl.properties]を設定して各使用モデルに使用するポリシーを指定し、そのポリシーファイルをプロパティで指定したディレクトリに配置し `config.resourcesDirectory` ます。

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

