---
seo-title: 非SWFアプリケーションの許可リスト
title: 非SWFアプリケーションの許可リスト
uuid: d4f93b15-e556-4749-95ab-f7f58b1061d7
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---


# 非SWFアプリケーションの許可リスト {#non-swf-application-isting}

AIRは、アプリケーションのリスト表示を特集した最初のプラットフォームで、SWF以外のアプリケーション（Adobe AIR、iOS、Androidなど）の許可リストに使用するプロパティの名前も は、元の名前を保持します。 `policy.allowedAIRApplication.n`. これにより、公開前に署名の証明書で署名されたFlash以外のすべてのアプリケーションでコンテンツを再生できます。 これを *アプリケーション IDと呼びます*。 アプリケーション IDは、この [!DNL AdobePublisherIDUtility.jar] ツールを使用して抽出できます。 これにより、Primetime DRMをサポートする任意のクライアントに対してリストが許可されます。

このアプリケーション IDは、特定のアプリケーションへの署名に使用される署名証明書の公開鍵から派生します。 証明書の公開鍵の有効期限が切れた場合、リストに表示されている過去のコンテンツはすべて、古い証明書で署名されたアプリでの再生のみが許可され、新しいアプリでは再生されません（新しい証明書で署名）。

特定の署名証明書で署名されたアプリケーションに対して許可されたコンテンツライブラリがあり、その証明書の期限が切れて新しい証明書が発行された場合（別の公開/秘密キーペアを使用）、次のいずれかを行わな *い限り、古いコンテンツは新しいアプリで再生されません* 。

* ライセンスサーバー `PolicyUpdateList` 上のを使用して、受信ポリシーを上書きし、新しい署名証明書のダイジェストを含む新しいアプリケーション許可リストエントリを挿入します。
* 受信ポリシーを上書きし、新しいアプリケーション許可リストエントリを挿入するように、ライセンスサーバーのロジックを更新します。
* 署名証明書の発行者に対し、以前の証明書と同じ公開/秘密キーペアを使用する新しい証明書を発行するように要求します。
* URLエンドポイントを参照するHDS/HLSコンテンツを配信してURLを取得する場合 `DRMMetadata`、 `DRMMetadata` （Primetime DRM Java SDKを使用して）を再生成し、更新されたアプリケーション許可リストエントリを含む新しいDRMポリシーを挿入できます。

* 新しい署名証明書のダイジェストを持つ新しいDRMポリシーを使用して、古いコンテンツをすべて再パッケージ化します。

詳し `policy.allowedAIRApplication.n` くは、 *設定プロパティの* 「」を参照してください。

>[!NOTE]
>
>iOSアプリケーションのリストを許可するには、特別な方法が必要です。 「TVSDK for iOS Programmer&#39;s Guide」のiOSアプリケーションの [許可リストを参照してください](../../../../../programming/tvsdk-3x-ios-prog/ios-3x-drm-content-security/ios-3x-allowlist-your-ios-application.md)**。
