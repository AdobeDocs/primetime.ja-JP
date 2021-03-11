---
description: PrimetimeDigital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションを、Adobeの統合Primetime DRMソリューションの代替として使用できます。
title: Primetime DRMインターフェイスの概要
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---


# 概要{#primetime-drm-interface-overview}

PrimetimeDigital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションを、Adobeの統合Primetime DRMソリューションの代替として使用できます。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

サードパーティのDRMソリューションの可用性に関する最新情報については、Adobeの担当者にお問い合わせください。

Primetime digital rights management(DRM)システムのクライアント側の主要要素はDRMマネージャーです。 Android SDKに含まれるサンプルアプリケーションには`DRMHelper`クラスが含まれており、このクラスは、特定のDRM操作の実装を簡単にする方法を示しています。

Primetime DRMは、TVSDKアプリケーションにコンテンツ保護を実装するためのスケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツの権限を保護し、管理します。

TVSDKパッケージに含まれるDRMサンプルプレイヤーコードを参照してください。

以下は、DRMを操作するための最も重要なAPI要素です。

* DRMサブシステムを実装するDRMマネージャーオブジェクトへのメディアプレイヤー内の参照：

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >このAPIは、`MediaPlayerEvent.DRM_METADATA`が呼び出された後にのみ有効な`DRMManager`オブジェクトを返します。 このイベントが起動する前に`getDRMManager()`を呼び出すと、NULLが返される場合があります。

* `DRMHelper`ヘルパークラス。DRMワークフローの実装時に役立ちます。

   `DRMHelper`は`ReferencePlayer`で確認できます。

* `DRMHelper`メタデータローダーメソッド。DRMメタデータがメディアとは別のURLにある場合に、そのメタデータを読み込みます。

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* DRMメタデータをチェックして認証が必要かどうかを判断する`DRMHelper`メソッド。

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

* `DRMHelper` 認証を実行する方法。

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

* 様々なDRMアクティビティとステータスをアプリに通知するイベント。

<!--<a id="section_899BD9061D484E1BBA46E84617C36867"></a>-->

関連するその他のAPIエレメント：

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

DRMについて詳しくは、[Adobe PrimetimeDRMドキュメント](https://helpx.adobe.com/primetime/user-guide.html)を参照してください。
