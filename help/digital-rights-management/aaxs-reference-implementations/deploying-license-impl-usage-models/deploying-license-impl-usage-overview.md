---
seo-title: 使用モデルの実装の概要
title: 使用モデルの実装の概要
uuid: 1041bb84-9996-4284-b2a0-d6fc6d4b73d9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 使用モデルの実装の概要 {#implementing-the-usage-models-overview}

リファレンスの実装には、パッケージ化されたコンテンツの1つに対して次の4つの異なる使用モデルを有効にする方法を示すビジネスロジックが含まれています。

* ダウンロード先(DTO)
* レンタル/ビデオオンデマンド(VOD)
* 購読（食べ放題）
* 広告が出資した

使用モデルのデモを有効にするには、パッケージ化時にカスタムプロパ `RI_UsageModelDemo=true` ティを指定します。 Media Packagerコマンドラインツールを使用してコンテンツをパッケージ化する場合は、次のように指定します。

```
    java -jar AdobeMediaPackager.jar source.flv dest.flv -k RI_UsageModelDemo=true
```

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>パッケージ化時にオプションのデモモードをアクティブ化しない場合、ライセンスサーバーはパッケージ化時に指定されたポリシーを使用してライセンスを発行します。 複数のポリシーを指定した場合、ライセンスサーバーは最初の有効なポリシーを使用します。

デモでは、サーバー上のビジネスロジックが、生成されたライセンスの実際の属性を制御します。 パッケージ化の際は、最小限のポリシー情報のみをコンテンツに含める必要があります。 具体的には、ポリシーは、コンテンツにアクセスするために認証が必要かどうかを示す必要があります。 4つの使用モデルをすべて有効にするには、匿名アクセスを許可する1つのポリシー（広告提供モデルの場合）と、ユーザー名/パスワード認証を必要とする1つのポリシー（他の3つの使用モデルの場合）を含めます。 ライセンスを要求する場合、クライアントアプリケーションは、ポリシー内の認証情報に基づいて、ユーザーに認証を求めるかどうかを決定できます。

特定のユーザにライセンスを発行する使用モデルを制御するために、参照実装データベースにエントリを追加できます。 この表に `Customer` は、ユーザーを認証するためのユーザー名とパスワードが含まれています。 また、ユーザーが購読を持っているかどうかも示されます。 購読を持つユーザーは、購読の使用モデルの下で *ライセンス* が発行されます。 「所有するビデオまたはオンデマンドビデオの ** 」の使用モデルでユーザーにアクセスを許可するには、ユーザーがアクセスを許可されるコンテンツの各部分と使用モデルを指定するエントリを表に追加します **`CustomerAuthorization` 。 各テーブルの入力につ [!DNL PopulateSampleDB.sql] いて詳しくは、スクリプトを参照してください。

ユーザーがライセンスを要求すると、参照実装サーバーは、クライアントから送信されたメタデータを調べて、コンテンツがプロパティを使用してパッケージ化されたかどうかを判断 `RI_UsageModelDemo` します。 その場合は、次のビジネスルールが使用されます。

* いずれかのポリシーで認証が必要な場合：

   * リクエストに有効な認証トークンが含まれている場合は、Customerデータベースの表でユーザーを探します。 ユーザーが見つかった場合：

      * プロパティ `Customer.IsSubscriber` がの場 `true`合は、 *Subscription* 使用モデルのライセンスを生成し、ユーザに送信します。

      * このユーザーとコンテンツIDのデ `CustomerAuthorization` ータベーステーブル内のレコードを探します。 レコードが見つかった場合：

         * の場合 `CustomerAuthorization.UsageType` は、 `DTO`「Download To Own *」使用モデルのライセンスを生成し* 、ユーザに送信します。

         * が有効 `CustomerAuthorization.UsageType` な場 `VOD`合は、 *Video On Demand使用モデルのライセンスを生成し* 、ユーザに送信します。
   * どのポリシーも匿名アクセスを許可しない場合：

      * 要求に有効な認証トークンがない場合は、「認証が必要です」というエラーを返します。
      * それ以外の場合は、「認証されていません」というエラーが返されます。


* ポリシーの1つで匿名アクセスが許可されている場合は、広告の出資による使用モデルのライセンスを生成し、ユーザーに送信します。

参照実装サーバーが使用モデルデモのライセンスを発行する前に、4つの使用モデルのそれぞれに対してライセンスを生成する方法を指定するようにサーバーを設定する必要があります。 これは、各使用モデルに対してポリシーを指定することで行われます。 リファレンスの実装には、4つのサンプルポリシー(、、、、 [!DNL dto-policy.pol]など [!DNL vod-policy.pol])が含まれているか、独自のポリシーに置き換え [!DNL sub-policy.pol][!DNL ad-policy.pol]ることができます。 で、次の [!DNL flashaccess-refimpl.properties]プロパティを設定して、各使用モデルに使用するポリシーを指定し、そのプロパティで指定したディレクトリにポリシーファイルを配置 `config.resourcesDirectory` します。

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

