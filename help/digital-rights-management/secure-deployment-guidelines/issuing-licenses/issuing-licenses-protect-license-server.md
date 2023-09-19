---
description: ライセンスを安全に発行していることを確認する必要があります。 ライセンスサーバを保護するために、次のベストプラクティスを検討します。
title: ライセンスサーバの保護
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1178'
ht-degree: 0%

---

# ライセンスサーバの保護 {#protecting-the-license-server}

ライセンスを安全に発行していることを確認する必要があります。 ライセンスサーバを保護するには、次のベストプラクティスを検討します。

## ローカルで生成された CRL の使用 {#consuming-locally-generated-crls}

ローカルに生成された証明書失効リスト (CRL) とポリシー更新リストを使用するには、Adobe Primetime DRM API を使用して署名を検証します。

次の API は、リストが改ざんされていないこと、およびリストが正しいライセンスサーバーによって署名されたことを確認します。

* 通話 [RevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) を使用して、 [RevocationList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) を任意の API に追加します。

  詳しくは、 [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

* 通話 [PolicyUpdateList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) 署名を確認してから `PolicyUpdateList` を任意の API に追加します。

  詳しくは、 [PolicyUpdateList](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html).

## Adobeが公開した CRL の使用{#consuming-crls-published-by-adobe}

SDK は、Adobeが公開した CRL を定期的にダウンロードします。 これらのファイルへのアクセスがブロックされないようにするか、これらの CRL の適用が妨げられないようにする必要があります。

SDK には、AdobeCRL の取得時にエラーを無視する設定オプションがあり、このオプションを適用できるのは開発環境のみです。 実稼動環境では、ライセンスサーバーはAdobeから CRL を取得する必要があります。 ライセンスサーバーが有効な CRL を取得できない場合は、エラーが発生しました。

## CRL を生成して、Adobeが発行したものを補完{#generating-crls-to-supplement-those-published-by-adobe}

Adobe Primetime DRM を使用して、Adobeが発行するマシン CRL を補完する CRL を作成できます。

Primetime DRM SDK は、AdobeCRL を確認し、強制します。 ただし、追加のクライアントマシンを許可しない場合は、CRL を Primetime DRM SDK に渡して、追加のマシン資格情報を無効にする CRL を作成します。 ライセンスを発行すると、SDK はAdobeCRL と CRL を確認します。

CRL を生成するには、 [RevocationListFactory](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html).

## ロールバック検出 {#rollback-detection}

Adobe Primetime DRM の実装で、クライアントに状態の維持を要求するビジネスルール（再生ウィンドウの間隔など）を使用する場合、Adobeでは、ロールバックカウンターを追跡し、AIRまたはSWFの許可リストを使用することをお勧めします。

ロールバックカウンターは、クライアントからのほとんどの要求でサーバーに送信されます。 Primetime DRM の実装にロールバックカウンターが必要ない場合は、そのカウンターを無視できます。 それ以外の場合は、Adobeは、を使用して取得されるランダムマシン ID をサーバーに保存することをお勧めします。 [MachineToken.getUniqueId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())、およびデータベース内の現在のカウンタ値。

ロールバックカウンタをインクリメントして追跡する方法の詳細については、 [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) およびロールバック検出。

## ライセンス発行時のコンピューター数 {#machine-count-when-issuing-licenses}

ビジネス・ルールでユーザーのマシン数を追跡する必要がある場合は、ライセンス・サーバーまたはドメイン・サーバーに、ユーザーに関連付けられたマシン ID を保存する必要があります。

マシン ID を追跡する最も堅牢な方法は、 [MachineId.getBytes()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) メソッドを使用して、データベース内で設定できます。 新しいリクエストを受け取ったら、を使用して、リクエスト内のマシン ID と既知のマシン ID を比較します。 [MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)).

[MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) は、ID の比較を実行して、ID が同じマシンを表しているかどうかを判断します。 この比較は、少数のマシン ID がある場合にのみ実用的です。 例えば、ユーザーがドメイン内で 5 台のマシンを許可されている場合は、データベースでユーザー名に関連付けられているマシン ID を検索し、比較用に小さなデータセットを取得できます。

この比較は、匿名アクセスを許可するデプロイメントには実用的ではありません。 この場合、 [MachineId.getUniqueID()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) を使用できます。 ただし、ユーザーがFlashとAdobe AIR®ランタイムからコンテンツにアクセスする場合、この ID を同じにすることはできません。

>[!NOTE]
>
>ユーザーが HDD を再フォーマットした場合、ID は有効になりません。

## リプレイの保護 {#replay-protection}

再生保護は、攻撃者がライセンスリクエストメッセージを再生し、潜在的に DoS(DoS) 攻撃をクライアントに対して発生させるのを防ぎます。

DoS 攻撃とは、攻撃者がサービスの正当なユーザーがそのサービスを使用するのを防ぐための試みです。 例えば、ロールバックカウンタを使用する再生攻撃は、DRM クライアントが状態をロールバックしたと考えるためにライセンスサーバを「騙す」ことができ、アカウントの停止を引き起こす可能性があります。

再生保護の詳細については、 [AbstractRequestMessage.getMessageId()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId()).

## 信頼できるコンテンツパッケージ許可リストの管理 {#maintain-a-allowlist-of-trusted-content-packagers}

許可リストは、信頼されたエンティティのリストです。

コンテンツパッケージャーの場合、エンティティとは、コンテンツ所有者がビデオファイルのパッケージ化（または暗号化）や DRM 保護されたコンテンツの作成を信頼できる組織です。 Adobe Primetime DRM をデプロイする場合は、信頼できるコンテンツパッケージャーの許可リストを維持する必要があります。 また、ライセンスを発行する前に、DRM 保護ファイルの DRM メタデータでコンテンツパッケージャの ID を確認する必要があります。

コンテンツをパッケージ化したエンティティに関する情報を取得する方法については、 [V2ContentMetaData.getPackagerInfo()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo()).

## 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

Adobe Primetime DRM SDK で生成されるすべての認証トークンには、アプリケーションのセキュリティを保護するためのタイムアウト間隔があります。

認証トークンの有効期限が指定されている場合は、認証リクエストの処理時に Primetime DRM SDK を使用します。 有効期限が切れた後、トークンは無効になり、ユーザーはライセンスサーバーで再認証する必要があります。

認証リクエストについて詳しくは、 [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html).

## ポリシーオプションの上書き {#overriding-policy-options}

ライセンスを発行すると、ライセンスサーバは、ポリシーで指定された使用規則を上書きできます。

ポリシーで開始日を指定した場合、その開始日より前にライセンスは生成されません。 ただし、ライセンスが生成された後に、ライセンスに将来の開始日を設定することができます。 このオプションは、ユーザーがシステム時間を前に移動して開始日を回避するのを防ぐことができないので、注意して使用する必要があります。
