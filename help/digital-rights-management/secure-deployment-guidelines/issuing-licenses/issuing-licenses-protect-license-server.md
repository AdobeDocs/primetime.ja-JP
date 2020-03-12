---
description: 'ライセンスを安全に発行していることを確認する必要があります。 ライセンスサーバを保護するために、次のベストプラクティスを検討します。 '
seo-description: 'ライセンスを安全に発行していることを確認する必要があります。 ライセンスサーバを保護するために、次のベストプラクティスを検討します。 '
seo-title: ライセンスサーバの保護
title: ライセンスサーバの保護
uuid: 7b5de17d-d0a7-41df-9651-4ff51c9965c6
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# ライセンスサーバの保護 {#protecting-the-license-server}

ライセンスを安全に発行していることを確認する必要があります。 ライセンスサーバを保護するには、次のベストプラクティスを検討します。

## ローカルに生成されたCRLの使用 {#consuming-locally-generated-crls}

ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、Adobe Primetime DRM APIを使用して署名を検証します。

次のAPIは、リストが改ざんされていないこと、およびリストが正しいLicense Serverによって署名されていることを確認します。

* RevocationList [をAPIに提供する前に](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) 、RevocationList.verifySignatureを呼び出して署名を確認 [します](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) 。

   詳しくは、RevocationListFactoryを参照して [ください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html)。

* PolicyUpdateList. [verifySignatureを呼び出し](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate)) 、APIを提供する前に署名を確 `PolicyUpdateList` 認します。

   詳しくは、PolicyUpdateListを参照してく [ださい](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html)。

## Adobeが発行したCRLの使用{#consuming-crls-published-by-adobe}

SDKは、アドビが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスがブロックされないようにするか、またはこれらのCRLの強制が妨げられないようにする必要があります。

SDKには、Adobe CRLを取得する際にエラーを無視する設定オプションがあり、このオプションは開発環境でのみ適用できます。 実稼働環境では、ライセンスサーバーはアドビからCRLを取得する必要があります。 ライセンスサーバーが有効なCRLを取得できない場合、エラーが発生しました。

## アドビが発行したCRLを補完するCRLの生成{#generating-crls-to-supplement-those-published-by-adobe}

Adobe Primetime DRMを使用して、Adobeによって発行されたマシンCRLを補完するCRLを作成できます。

Primetime DRM SDKはAdobe CRLを確認し、強制します。 ただし、追加のクライアントコンピューターを許可しないようにするには、CRLを作成し、CRLをPrimetime DRM SDKに渡すことで、追加のコンピューター資格情報を失効させます。 ライセンスを発行すると、SDKはAdobe CRLとCRLを確認します。

CRLを生成するには、RevocationListFactoryを参照し [てください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html)。

## ロールバックの検出 {#rollback-detection}

Adobe Primetime DRMの実装で、クライアントが状態（再生ウィンドウの間隔など）を維持する必要があるビジネスルールを使用する場合、サーバーでロールバックカウンターを追跡し、AIRまたはSWFホワイトリストを使用することをお勧めします。

rollbackカウンタは、クライアントからのほとんどの要求でサーバに送信されます。 Primetime DRMの実装にロールバックカウンターが不要な場合は、無視できます。 それ以外の場合は、MachineToken.getUniqueId()を使用して取得したランダムなマシンIDと、現在のカウンター値をデータベースに格納することをアドビは [](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())、サーバーに推奨します。

ロールバックカウンターを増分および追跡する方法の詳細については、 [ClientState](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) and Rollback detectionを参照してください。

## ライセンス発行時のコンピューター数 {#machine-count-when-issuing-licenses}

ビジネスルールでユーザーのマシン数を追跡する必要がある場合、ライセンスサーバーまたはドメインサーバーには、そのユーザーに関連付けられたマシンIDを格納する必要があります。

マシンIDを追跡する最も強力な方法は、 [MachineId.getBytes()メソッドによって返される値をデータベースに格納することです](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) 。 新しい要求を受け取った場合、MachineId.matches()を使用して、要求内のマシンIDと既知のマシンID [を比較します](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId))。

[MachineId.matches()は](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) 、IDの比較を実行して、IDが同じマシンを表しているかどうかを判断します。 この比較は、マシンIDの数が少ない場合にのみ実用的です。 例えば、ユーザーがドメイン内で5台のマシンを使用できる場合は、データベースでそのユーザーのユーザー名に関連付けられているマシンIDを検索し、比較用の小さなデータセットを取得できます。

この比較は、匿名アクセスを許可するデプロイメントでは実用的ではありません。 この場合、 [MachineId.getUniqueID()を使用できます](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) 。 ただし、ユーザーがFlashおよびAdobe AIR®ランタイムからコンテンツにアクセスした場合、このIDは同じにできません。

>[!NOTE]
>
>IDは、ユーザーがハードドライブを再フォーマットした場合には保持されません。

## 再生保護 {#replay-protection}

再生保護を使用すると、攻撃者がライセンス要求メッセージを再生したり、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぐことができます。

DoS攻撃とは、攻撃者がサービスの正当なユーザーがそのサービスを使用できないようにする試みです。 例えば、ロールバックカウンターを使用するリプレイ攻撃を使用して、DRMクライアントが状態をロールバックしたと判断し、アカウントが停止する原因となるように、ライセンスサーバーを「騙し」取ることができます。

再生保護について詳しくは、AbstractRequestMessage.getMessageId() [ を参照してください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId())。

## 信頼できるコンテンツパッケージャーのホワイトリストの管理{#maintain-a-whitelist-of-trusted-content-packagers}

ホワイトリストは、信頼できるエンティティのリストです。

コンテンツパッケージャーの場合、エンティティは、ビデオファイルをパッケージ化（または暗号化）し、DRM保護されたコンテンツを作成するために、コンテンツ所有者に信頼される組織です。 Adobe Primetime DRMをデプロイする場合は、信頼できるコンテンツパッケージャーのホワイトリストを維持する必要があります。 また、ライセンスを発行する前に、DRM保護ファイルのDRMメタデータでコンテンツパッケージャーのIDを確認する必要があります。

コンテンツをパッケージ化したエンティティに関する情報を取得する方法については、 [V2ContentMetaData.getPackagerInfo()を参照してください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo())。

## 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

Adobe Primetime DRM SDKによって生成されるすべての認証トークンには、アプリケーションセキュリティを保護するためのタイムアウト間隔があります。

認証トークンの有効期限は、認証要求を処理する際にPrimetime DRM SDKを使用して指定されます。 有効期限が切れると、トークンは無効になり、ユーザーはライセンスサーバーを使用して再度認証する必要があります。

認証要求について詳しくは、AuthenticationHandlerを参照して [ください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html)。

## ポリシーオプションの上書き {#overriding-policy-options}

ライセンスを発行すると、ポリシーで指定された使用規則をライセンスサーバーが上書きできます。

ポリシーで開始日を指定した場合、その開始日より前のライセンスは生成されません。 ただし、ライセンスの生成後に、ライセンスの将来の開始日を設定することができます。 このオプションは、ユーザーが開始日を回避するためにシステム時間を前に移動するのを防ぐことができないので、注意して使用してください。