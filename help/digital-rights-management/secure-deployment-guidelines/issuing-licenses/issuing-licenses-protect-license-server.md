---
description: 'ライセンスを安全に発行していることを確認する必要があります。 License Serverを保護するには、以下のベストプラクティスを検討します。 '
seo-description: 'ライセンスを安全に発行していることを確認する必要があります。 License Serverを保護するには、以下のベストプラクティスを検討します。 '
seo-title: ライセンスサーバの保護
title: ライセンスサーバの保護
uuid: 7b5de17d-d0a7-41df-9651-4ff51c9965c6
translation-type: tm+mt
source-git-commit: 9d2e046ae259c05fb4c278f464c9a26795e554fc
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 0%

---


# ライセンスサーバの保護 {#protecting-the-license-server}

ライセンスを安全に発行していることを確認する必要があります。 License Serverを保護するには、次のベストプラクティスを検討します。

## ローカルに生成されたCRLの使用 {#consuming-locally-generated-crls}

ローカルに生成された証明書失効リスト(CRL)およびポリシー更新リストを使用するには、Adobe Primetime DRM APIを使用して署名を検証します。

次のAPIは、リストが改ざんされていないこと、およびリストが正しいLicense Serverによって署名されていることを確認します。

* RevocationList [をAPIに提供する前にRevocationList.verifySignature](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html#verifySignature(java.security.cert.X509Certificate)) を呼び出して署名を確認し [](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationList.html) ます。

   詳しくは、「RevocationListFactory [」を参照してください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html)。

* APIに署名を提供する前にPolicyUpdateList.verifySignature [を呼び出して署名](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html#verifySignature(java.security.cert.X509Certificate))`PolicyUpdateList` を確認します。

   詳しくは、PolicyUpdateListを参照して [ください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/policyupdate/PolicyUpdateList.html)。

## Adobeが発行したCRLの使用{#consuming-crls-published-by-adobe}

SDKは、アドビが発行したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしないようにするか、これらのCRLの適用を妨げないようにする必要があります。

SDKには、Adobe CRLを取得するときにエラーを無視する設定オプションがあり、このオプションは開発環境でのみ適用できます。 実稼働環境では、ライセンスサーバーはアドビからCRLを取得する必要があります。 ライセンスサーバーが有効なCRLを取得できない場合は、エラーが発生しました。

## アドビが発行するCRLを補完するCRLの生成{#generating-crls-to-supplement-those-published-by-adobe}

Adobe Primetime DRMを使用して、アドビが発行するマシンCRLを補完するCRLを作成できます。

Primetime DRM SDKがAdobe CRLを確認し、強制します。 ただし、追加のクライアントコンピューターを許可しない場合は、CRLをPrimetime DRM SDKに渡すことで、追加のコンピューターの秘密鍵証明書を失効させるCRLを作成します。 ライセンスを発行すると、SDKはAdobe CRLとCRLを確認します。

CRLを生成するには、RevocationListFactoryを参照して [ください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/revocation/RevocationListFactory.html)。

## ロールバックの検出 {#rollback-detection}

Adobe Primetime DRMの実装で、クライアントが状態（再生ウィンドウの間隔など）を維持する必要があるビジネスルールを使用する場合、サーバーはロールバックカウンターを追跡し、AIRまたはSWFで許可リストを使用することを推奨します。

rollbackカウンタは、クライアントからの要求の大部分で、サーバに送信されます。 Primetime DRMの実装にロールバックカウンターが必要ない場合は、無視できます。 それ以外の場合は、MachineToken.getUniqueId()を使用して取得したランダムなマシンIDと、現在のカウンター値をデータベースに格納する [ことをアドビは推奨します](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId())。

ロールバックカウンタを増分および追跡する方法の詳細については、「ClientState [](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/ClientState.html) and Rollback detection」を参照してください。

## ライセンス発行時のコンピュータ数 {#machine-count-when-issuing-licenses}

ビジネスルールでユーザーのマシン数を追跡する必要がある場合、License Serverまたはドメインサーバーには、ユーザーに関連付けられたマシンIDを格納する必要があります。

マシンIDを追跡する最も堅牢な方法は、MachineId.getBytes() [メソッドが返す値をデータベースに格納することです](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getBytes()) 。 新しい要求を受け取った場合は、MachineId.matches()を使用して、要求内のマシンIDと既知のマシンIDを比較 [します](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId))。

[MachineId.matches()](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#matches(com.adobe.flashaccess.sdk.cert.MachineId)) は、IDの比較を実行して、IDが同じマシンを表しているかどうかを判断します。 この比較は、マシンIDの数が少ない場合にのみ実用的です。 例えば、ドメインに5台のマシンを許可している場合、データベースでそのユーザーのユーザー名に関連付けられているマシンIDを検索し、比較用に小さなデータセットを取得できます。

この比較は、匿名アクセスを許可するデプロイメントでは実用的ではありません。 この場合、 [MachineId.getUniqueID()を使用でき](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/cert/MachineId.html#getUniqueId()) ます。 ただし、ユーザーがFlashおよびAdobe AIR®ランタイムからコンテンツにアクセスした場合、このIDを同じにすることはできません。

>[!NOTE]
>
>IDは、ユーザーがハードドライブの形式を変更した場合には保持されません。

## 再生保護 {#replay-protection}

リプレイ保護は、攻撃者がライセンス要求メッセージを再生するのを防ぎ、場合によってはクライアントに対するサービス拒否(DoS)攻撃を引き起こすのを防ぎます。

DoS攻撃とは、攻撃者がサービスの正当なユーザーがそのサービスを使用できないようにする試みです。 例えば、ロールバックカウンターを使用するリプレイ攻撃を使用して、DRMクライアントが状態をロールバックしたと判断して、License Serverを「騙し取り」、アカウントを停止させることができます。

リプレイ保護の詳細については、AbstractRequestMessage.getMessageId()を参照してくだ [ さい](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/AbstractRequestMessage.html#getMessageId())。

## 信頼できるコンテンツパッケージャーの許可リストの管理{#maintain-a-allowlist-of-trusted-content-packagers}

許可リストとは、信頼されたエンティティのリストです。

コンテンツパッケージャーの場合、エンティティは、コンテンツ所有者に信頼されて、ビデオファイルのパッケージ化（または暗号化）やDRM保護コンテンツの作成を行う組織です。 Adobe Primetime DRMをデプロイする場合は、信頼できるコンテンツパッケージャーの許可リストを維持する必要があります。 また、ライセンスを発行する前に、DRM保護ファイルのDRMメタデータ内のコンテンツパッケージャーのIDを検証する必要があります。

コンテンツをパッケージ化したエンティティに関する情報を取得する方法については、 [V2ContentMetaData.getPackagerInfo()を参照してください](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/media/drm/keys/v2/V2ContentMetaData.html#getPackagerInfo())。

## 認証トークンのタイムアウト{#timeout-for-authentication-tokens}

Adobe Primetime DRM SDKによって生成されるすべての認証トークンには、アプリケーションのセキュリティを保護するためのタイムアウト間隔があります。

認証トークンの有効期限は、認証要求を処理する際にPrimetime DRM SDKを使用して指定されます。 有効期限が切れると、トークンは無効になり、ユーザーはライセンスサーバーで再認証する必要があります。

認証要求について詳しくは、「 [AuthenticationHandler](https://help.adobe.com/en_US/primetime/api/drm-apis/server/javadocs-flashaccess-pro/com/adobe/flashaccess/sdk/protocol/authentication/AuthenticationHandler.html)」を参照してください。

## ポリシーオプションの上書き {#overriding-policy-options}

ライセンスを発行すると、ポリシーで指定されている使用規則をライセンスサーバーが上書きできます。

ポリシーで開始日を指定した場合、その開始日より前にライセンスは生成されません。 ただし、ライセンスの生成後に、ライセンスの将来の開始日を設定することはできます。 このオプションは、開始日を回避するためにクライアントがシステム時間を前に移動するのを防ぐことができないので、注意して使用してください。