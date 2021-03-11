---
description: Primetime DRMソリューションのクライアント側の主要要素はDRMマネージャーです。 Android SDKに含まれるサンプルアプリケーションには、特定のDRM操作をより簡単に実装できるようにするためのDRMHelperクラスも含まれています。
title: Primetime DRMインターフェイスの概要
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---


# Primetime DRMインターフェイスの概要{#primetime-drm-interface-overview}

Primetime DRMソリューションのクライアント側の主要要素はDRMマネージャーです。 Android SDKに含まれるサンプルアプリケーションには、特定のDRM操作をより簡単に実装できるようにするためのDRMHelperクラスも含まれています。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRMは、TVSDKアプリケーションにコンテンツ保護を実装するためのスケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツの権限を保護し、管理します。

詳しくは、TVSDKパッケージに含まれているDRMサンプルプレイヤーコードを参照してください。

DRMを操作するための最も重要なAPI要素を次に示します。

* DRMサブシステムを実装するDRMマネージャーオブジェクトへのメディアプレイヤー内の参照：

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >このAPIは、`MediaPlayerEvent.DRM_METADATA`が呼び出された後にのみ有効な`DRMManager`オブジェクトを返します。 このイベントが起動する前に`getDRMManager()`を呼び出すと、NULLが返される場合があります。

* `DRMHelper`ヘルパークラス。DRMワークフローの実装時に役立ちます。
* `DRMHelper`メタデータローダーメソッド。DRMメタデータがメディアとは別のURLにある場合に、そのメタデータを読み込みます。

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* DRMメタデータをチェックし、認証が必要かどうかを判断する`DRMHelper`メソッド。

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

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

DRMについて詳しくは、[DRMドキュメント](https://helpx.adobe.com/primetime/user-guide.html)を参照してください。
