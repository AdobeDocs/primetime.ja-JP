---
title: 事前に実行する環境とテストの設定
description: 事前に実行する環境とテストの設定
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---


# 事前に実行する環境とテストの設定{#setting-up-your-environment-and-testing-in-prequal}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

このテクニカルノートの目的は、パートナーが環境を設定し、Adobeの事前認定環境にデプロイされた新しいビルドのテストを開始するのを支援することです。

ビルドには 2 種類あるので、次のようにします。 ***実稼動*** および ***ステージング***&#x200B;このドキュメントでは、実稼動の設定に焦点を当てます。ここでは、すべての手順がステージングで同じで、URL のみが異なるという点に言及します。

手順 1 と 2 は、テストマシンの 1 つにテスト環境を設定し、手順 3 は基本的なフローの検証で、手順 4 と 5 は、いくつかのテストガイドラインを示しています。

>[!IMPORTANT]
>
> テスト環境を変更するたび（ステージングから実稼動プロファイルへの切り替えまたはその他の方法）に、手順 1 および 2 を実行することが非常に重要です。
 

## 手順 1. IP へのパスドメインの解決 {#resolving-pass-domain-to-an-ip}

* スプーフィングに使用できるロードバランサー IP を見つけるには、次のコマンドを実行します。

* **Windows の場合**

   ```cmd
   C:\>nslookup sp-prequal.auth.adobe.com
   ...
   Addresses:  52.13.71.11
               54.184.208.150
   ```

```Choose any IP from **addresses** section (e.g. `52.13.71.11)```

* **Linux/Macの場合**

```sh
    $ dig sp-prequal.auth.adobe.com
    
    ;; ANSWER SECTION:
    ...
    ............ 60 IN A      52.13.71.11
    ............ 60 IN A      54.184.208.150
```

```Choose any IP from **A records (**e.g `52.13.71.11)```

>[!NOTE]
>
>関連性がないので、回答から除外されたドメインは、ユーザーによって異なる場合があります。

>[!IMPORTANT]
>
> これらの IP アドレスは、将来的に変更される可能性があり、異なる地域のユーザーでは同じでない可能性があります。


## 手順 2.  実稼動環境にする事前認定環境のスプーフィング {#spoofing-the-prequalification-environment}

* を編集します。 *c:\\windows\\System32\\drivers\\etc\\hosts* ファイル（Windows の場合）または */etc/hosts* ファイル (Macintosh、Linux、Android) に次のコードを追加します。

* スプーフ実稼動プロファイル
   * 52.13.71.11 http://entitlement.auth.adobe.com, http://sp.auth.adobe.com, http://api.auth.adobe.com

**Android でのスプーフィング：** Android でスプーフィングを行うには、Android エミュレーターを使用する必要があります。

* スプーフィングを設定したら、次のように、実稼動およびステージングプロファイルに通常の URL を使用するだけで済みます。( つまり `http://sp.auth-staging.adobe.com` および `http://entitlement.auth-staging.adobe.com` そして実際に *事前認定環境/実稼動環境* *の新しいビルドの。


## 手順 3.  適切な環境を指していることを確認します。 {#Verify-you-are-pointing-to-the-right-environment}

**これは簡単な手順です。**

* 負荷 [権利前期環境](https://entitlement-prequal.auth.adobe.com/environment.html) および [権利付与](https://entitlement.auth.adobe.com/environment.html). 同じ応答を返す必要があります。


## 手順 4.  プログラマーの Web サイトを使用して、簡単な認証/承認フローを実行します {#peform-a-simple-auth-flow}

* この手順には、プログラマーの Web サイトアドレスと、有効な MVPD 認証情報（認証済みで認証済みのユーザー）が必要です。

## 手順 5.  プログラマーの Web サイトを使用してシナリオテストを実行する {#perform-scenario-testing-using-programmer-website}

* 環境の設定を完了し、基本的な認証/承認フローが機能していることを確認したら、より複雑なシナリオのテストを進めることができます。


## 手順 6.  API テストサイトを使用したテストの実行 {#perform-testing-using-api-testing-site}

* Adobe Primetime認証のテストを詳しく調べるには、 [API テストサイト](http://entitlement-prequal.auth.adobe.com/apitest/api.html).

API テストサイトの詳細は、 [Adobeの API テストサイトを使用した認証フローと承認フローのテスト方法](/help/authentication/test-authn-authz-flows-using-adobes-api-test-site.md).

