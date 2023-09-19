---
title: 非SWFアプリの許可リストへの登録
description: 非SWFアプリの許可リストへの登録
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# 非SWFアプリの許可リストへの登録 {#non-swf-application-isting}

AIRは、SWFの許可リストへの登録を取り上げた最初のプラットフォームで、アプリケーション以外のアプリケーション (Adobe AIR、iOS、Android など ) の許可リストに使用するプロパティの名前 は元の名前を保持します。 `policy.allowedAIRApplication.n`. これにより、公開前に署名の証明書を使用して署名された、Flash以外のすべてのアプリケーションでコンテンツを再生できます。 これは、 *アプリケーション ID*. アプリケーション ID は、 [!DNL AdobePublisherIDUtility.jar] ツールを使用します。 これにより、Primetime DRM をサポートする任意のクライアントで許可リストが適用されます。

アプリケーション ID は、特定のアプリケーションへの署名に使用される署名証明書の公開鍵から生成されます。 証明書の公開鍵が期限切れになった場合、以前にリストされたすべてのコンテンツで、古い証明書で署名されたアプリでのみ再生できます（新しい証明書で署名）。

特定の署名証明書で署名されたアプリケーションに対してコンテンツのライブラリを許可リストに登録し、その証明書の有効期限が切れて新しい証明書（公開鍵と秘密鍵のペアが異なる）が発行された場合、古いコンテンツは新しいアプリでは再生されません *unless* 次のいずれかの操作を行います。

* の使用 `PolicyUpdateList` を使用して、受信ポリシーを上書きし、新しい署名許可リストのダイジェストを使用して新しいアプリケーションポリシーエントリを挿入します。
* 受信ポリシーを上書きし、新しいアプリケーション許可リストを挿入するには、ライセンスサーバーのロジックを更新します。
* 署名証明書発行者が、以前の証明書で使用したものと同じ公開鍵/秘密鍵のペアを使用する新しい証明書を発行するように要求します。
* URL エンドポイントを参照する HDS/HLS コンテンツを配信して、 `DRMMetadata`を再生成すると、 `DRMMetadata` （Primetime DRM Java SDK を使用）を使用して、更新されたアプリケーション許可リストエントリを含む新しい DRM ポリシーを挿入します。

* 新しい署名証明書のダイジェストを含む新しい DRM ポリシーを使用して、古いコンテンツをすべて再パッケージ化します。

詳しくは、 `policy.allowedAIRApplication.n` in *設定プロパティ* 」を参照してください。

>[!NOTE]
>
>iOSアプリケーションを許可リストに登録するには、特別な方法が必要です。 詳しくは、 [iOSアプリケーションの許可リスト](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md) （内） *TVSDK for iOSプログラマーズガイド*.
