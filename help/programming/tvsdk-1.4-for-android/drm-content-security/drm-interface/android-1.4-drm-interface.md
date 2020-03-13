---
description: Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 また、サードパーティのDRMソリューションをアドビの統合Primetime DRMソリューションの代わりに使用することもできます。
seo-description: Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 また、サードパーティのDRMソリューションをアドビの統合Primetime DRMソリューションの代わりに使用することもできます。
seo-title: Primetime DRMインターフェイスの概要
title: Primetime DRMインターフェイスの概要
uuid: 71479464-8356-4732-9774-da9f6084e6ad
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 概要 {#primetime-drm-interface-overview}

Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 また、サードパーティのDRMソリューションをアドビの統合Primetime DRMソリューションの代わりに使用することもできます。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

サードパーティのDRMソリューションの可用性に関する最新情報については、アドビの担当者にお問い合わせください。

Primetimeデジタル著作権管理(DRM)システムのクライアント側の主要な要素は、DRMマネージャーです。 Android SDKに付属のサンプルアプリケーションには、特定のDRM操 `DRMHelper` 作をより簡単に実装できるようにする方法を示すクラスが含まれています。

Primetime DRMは、TVSDKアプリケーションにコンテンツ保護を実装するための、スケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツの権限を保護し、管理します。

TVSDKパッケージに含まれているDRMサンプルプレイヤーコードを参照してください。

DRMを操作するための最も重要なAPI要素は次のとおりです。

* DRMサブシステムを実装するDRMマネージャーオブジェクトへのメディアプレイヤー内の参照：

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >このAPIは、が呼び出された後にの `DRMManager` み有効なオブジェクトを `MediaPlayerEvent.DRM_METADATA` 返します。 このイベントが発生す `getDRMManager()` る前にを呼び出すと、NULLが返される場合があります。

* DRMワー `DRMHelper` クフローを実装する場合に役立つヘルパークラス。

   はを参照してく `DRMHelper` ださ `ReferencePlayer`い。

* DRMメタ `DRMHelper` データがメディアとは別のURLに配置されている場合にDRMメタデータを読み込むメタデータローダーメソッドです。

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* DRMメタ `DRMHelper` データをチェックして、認証が必要かどうかを判断するメソッドです。

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

* 様々なDRMアクティビティとステータスをアプリケーションに通知するイベント。

<!--<a id="section_899BD9061D484E1BBA46E84617C36867"></a>-->

関連するその他のAPI要素：

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

DRMについて詳しくは、 [Adobe Primetime DRMのドキュメントを参照してください](https://helpx.adobe.com/primetime/user-guide.html)。
