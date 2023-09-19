---
title: 事前に実行する環境とテストの設定
description: 事前に実行する環境とテストの設定
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# 環境の設定と前提のテスト{#setting-up-your-environment-and-testing-in-prequal}

>[!NOTE]
>
>このページの内容は、情報目的でのみ提供されています。 この API を使用するには、Adobe Systems の現在のライセンス版が必要です。 権限のない使用は許可されていません。

この技術メモの目的は、パートナーが環境を設定し、Adobe Systems 事前認定環境に導入された新しいビルドのテストを開始できるようにすることです。

ビルドフレーバーは2つあります。 ***実稼動環境*** と ***ステージング*** 環境の場合、このドキュメントでは、すべての手順がステージングの場合と同じであり、url だけが異なることを説明するために、実稼働用のセットアップにフォーカスするします。

手順1と2では、テスト用のコンピューターのいずれかでテスト環境を設定しています。手順3は基本的なフローを検証し、5番目の手順では、いくつかのテストガイドラインを示しています。

>[!IMPORTANT]
>
> テスト環境を変更する場合は、手順1と2を毎回実行する必要があります (ステージングから実稼働への切り替えプロファイルまたはその他の方法)。


## 手順 1. IP に渡すドメインの解決 {#resolving-pass-domain-to-an-ip}

* スプーフィングに使用できるロードバランサー IP を見つけるには、次のコマンドを実行します。

* **Windows の場合**

  ```cmd
  C:\>nslookup sp-prequal.auth.adobe.com
  ...
  Addresses:  52.13.71.11
              54.184.208.150
  ```

```Choose any IP from **addresses** section (e.g. `52.13.71.11)```

* **Linux/Mac**

```sh
    $ dig sp-prequal.auth.adobe.com
    
    ;; ANSWER SECTION:
    ...
    ............ 60 IN A      52.13.71.11
    ............ 60 IN A      54.184.208.150
```

```Choose any IP from **A records (**e.g `52.13.71.11)```

>[!NOTE]
>
>関連性がないので、~に回答から除外されたドメインは、ユーザーとユーザーが異なる可能性があります。

>[!IMPORTANT]
>
> これらの IP アドレスは将来変更される可能性があり、地理的に異なる地域のユーザーに対しては同じでない場合があります。


## 手順 2.  運用のための事前認定環境のスプーフィング {#spoofing-the-prequalification-environment}

* *C:\\windows\\System32\\drivers\\etc\\hosts* ファイル (windows) または */Etc/hosts* ファイル (Macintosh/Linux/Android) を編集し、次の項目を追加します。

* スプーフィング運用プロファイル
   * 52.13.71.11 http://entitlement.auth.adobe.com, http://sp.auth.adobe.com, http://api.auth.adobe.com

**Android でのスプーフィング：** Android でスプーフィングを行うには、Android エミュレーターを使用する必要があります。

* スプーフィングを設定したら、次のように、実稼動およびステージングプロファイルの通常の URL を使用できます ( つまり、 `http://sp.auth-staging.adobe.com` および `http://entitlement.auth-staging.adobe.com` そして実際に *事前認定環境/実稼動環境* *の新しいビルドの。


## 手順 3.  適切な環境を指していることを確認します。 {#Verify-you-are-pointing-to-the-right-environment}

**これは簡単な手順です。**

* 受給 prequal 環境 ](https://entitlement-prequal.auth.adobe.com/environment.html) および受給資格 ](https://entitlement.auth.adobe.com/environment.html) を [ 読み込み [ ます。同じ応答を返す必要があります。


## 手順 4.  プログラマの web サイトを使用してシンプルな認証/認証フローを実行します。 {#peform-a-simple-auth-flow}

* この手順では、プログラマーズの web サイトアドレスと、いくつかの有効な MVPD 資格情報 (認証および承認されていることがユーザー) が必要です。

## 手順 5.  プログラマの web サイトを使用してシナリオテストを実行する {#perform-scenario-testing-using-programmer-website}

* 環境設定を完了し、基本認証認証のフローが機能していることを確認したら、より複雑なシナリオのテストに進むことができます。


## 手順 6.  API テストサイトを使用したテストの実行 {#perform-testing-using-api-testing-site}

* Adobe Primetime認証のテストを詳しく調べるには、 [API テストサイト](http://entitlement-prequal.auth.adobe.com/apitest/api.html).

API テストサイトの詳細は、 [Adobeの API テストサイトを使用した認証フローと承認フローのテスト方法](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).
