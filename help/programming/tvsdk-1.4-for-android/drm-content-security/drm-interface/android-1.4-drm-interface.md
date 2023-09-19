---
description: PrimetimeDigital Rights Management(DRM) システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティの DRM ソリューションを、Adobeの統合 Primetime DRM ソリューションの代わりに使用することもできます。
title: Primetime DRM インターフェイスの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# 概要 {#primetime-drm-interface-overview}

PrimetimeDigital Rights Management(DRM) システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティの DRM ソリューションを、Adobeの統合 Primetime DRM ソリューションの代わりに使用することもできます。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

サードパーティの DRM ソリューションの入手に関する最新情報については、Adobeの担当者にお問い合わせください。

Primetime デジタル著作権管理 (DRM) システムの主なクライアント側要素は DRM マネージャーです。 Android SDK に含まれているサンプルアプリケーションには、が含まれています。 `DRMHelper` 特定の DRM 操作を実装しやすくする方法を示すクラス。

Primetime DRM は、TVSDK アプリケーションにコンテンツ保護を実装するためのスケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツに対する権限を保護および管理できます。

TVSDK パッケージに含まれている DRM サンプルプレイヤーコードを参照してください。

DRM を操作するための最も重要な API 要素は次のとおりです。

* DRM サブシステムを実装する DRM マネージャーオブジェクトへのメディアプレーヤー内の参照。

  ```java
  MediaPlayer.getDRMManager();
  ```

  >[!TIP]
  >
  >この API は有効な `DRMManager` オブジェクトが `MediaPlayerEvent.DRM_METADATA` が起動されます。 を呼び出す場合 `getDRMManager()` このイベントが発生する前に、NULL が返される場合があります。

* The `DRMHelper` ヘルパークラス。DRM ワークフローを実装する際に役立ちます。

  次のように表示されます。 `DRMHelper` in `ReferencePlayer`.

* A `DRMHelper` メタデータローダーメソッド。DRM メタデータがメディアとは別の URL に配置されている場合に、そのメタデータを読み込みます。

  ```java
  public static void loadDRMMetadata(final DRMManager drmManager,  
     final String drmMetadataUrl,  
     final DRMLoadMetadataListener loadMetadataListener);
  ```

* A `DRMHelper` メソッドを使用して DRM メタデータを確認し、認証が必要かどうかを判断します。

  ```java
  /** 
  * Return whether authentication is needed for the provided 
  * DRMMetadata. 
  * 
  * @param drmMetadata 
  * The desired DRMMetadata on which to check whether auth is needed. 
  * @return whether authentication is required for the provided metadata 
  */ 
  public static boolean isAuthNeeded(DRMMetadata drmMetadata);
  ```

* `DRMHelper` メソッドを使用して認証を実行します。

  ```java
  /** 
  * Helper method to perform DRM authentication. 
  * 
  * @param drmManager 
  * the DRMManager, used to perform the authentication. 
  * @param drmMetadata 
  * the DRMMetadata, containing the DRM specific information. 
  * @param authenticationListener 
  * the listener, on which the user can be notified about the 
  * authentication process status. 
  * @param authUser 
  * the DRM username provider by the user. 
  * @param authPass 
  * the DRM password provided by the user. 
  */ 
  public static void performDrmAuthentication(final DRMManager drmManager,  
  final DRMMetadata drmMetadata,  
  final String authUser,  
  final String authPass,  
  final DRMAuthenticationListener authenticationListener);
  ```

* 様々な DRM アクティビティとステータスに関してアプリケーションに通知するイベント。

<!--<a id="section_899BD9061D484E1BBA46E84617C36867"></a>-->

関連するその他の API エレメント：

* [com.adobe.ave.drm.DRMManager](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMManager.html)
* [com.adobe.ave.drm.DRMMetdata](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMMetadata.html)
* [com.adobe.ave.drm.DRMPolicy](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMPolicy.html)
* [com.adobe.ave.drm.DRMAuthenticationMethod](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationMethod.html)
* [com.adobe.ave.drm.DRMAuthenticationCompleteCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMAuthenticationCompleteCallback.html)
* [com.adobe.ave.drm.DRMOperationErrorCallback](https://help.adobe.com/en_US/primetime/api/drm/com/adobe/ave/drm/DRMOperationErrorCallback.html)
* com.adobe.mediacore.drm.DRMAuthenticateListener

<!-- 
Comment Type: draft
(https://help.adobe.com/en_US/primetime/api/psdk/javadoc_2.4/com/adobe/mediacore/drm/DRMAuthenticateListener.html)

-->
<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

DRM について詳しくは、 [Adobe Primetime DRM ドキュメント](https://helpx.adobe.com/primetime/user-guide.html).
