---
description: Primetime DRMソリューションのクライアント側の主要な要素は、DRMマネージャーです。 Android SDKに含まれるサンプルアプリケーションには、特定のDRM操作をより簡単に実装できるようにするためのDRMHelperクラスも含まれています。
seo-description: Primetime DRMソリューションのクライアント側の主要な要素は、DRMマネージャーです。 Android SDKに含まれるサンプルアプリケーションには、特定のDRM操作をより簡単に実装できるようにするためのDRMHelperクラスも含まれています。
seo-title: Primetime DRMインターフェイスの概要
title: Primetime DRMインターフェイスの概要
uuid: d77a98c8-c1f5-4fe3-8d0b-3d21e288f228
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# Primetime DRMインターフェイスの概要 {#primetime-drm-interface-overview}

Primetime DRMソリューションのクライアント側の主要な要素は、DRMマネージャーです。 Android SDKに含まれるサンプルアプリケーションには、特定のDRM操作をより簡単に実装できるようにするためのDRMHelperクラスも含まれています。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRMは、TVSDKアプリケーションにコンテンツ保護を実装するための、スケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツの権限を保護し、管理します。

詳しくは、TVSDKパッケージに含まれているDRMサンプルプレイヤーコードを参照してください。

DRMを操作する上で最も重要なAPI要素を次に示します。

* DRMサブシステムを実装するDRMマネージャーオブジェクトへのメディアプレイヤー内の参照：

   ```java
   MediaPlayer.getDRMManager();
   ```

   >[!TIP]
   >
   >このAPIは、が呼び出された後にの `DRMManager` み有効なオブジェクトを `MediaPlayerEvent.DRM_METADATA` 返します。 このイベントが発生す `getDRMManager()` る前にを呼び出すと、NULLが返される場合があります。

* DRMワー `DRMHelper` クフローを実装する場合に役立つヘルパークラス。
* DRMメタ `DRMHelper` データがメディアとは別のURLに配置されている場合にDRMメタデータを読み込むメタデータローダーメソッドです。

   ```java
   public static void loadDRMMetadata(final DRMManager drmManager,  
      final String drmMetadataUrl,  
      final DRMLoadMetadataListener loadMetadataListener);
   ```

* DRMメタ `DRMHelper` データを確認し、認証が必要かどうかを判断する方法。

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

<!--<a id="section_F58941D68EB94A5EBD1C7454D2A1B17A"></a>-->

DRMについて詳しくは、 [DRMのドキュメントを参照してください](https://helpx.adobe.com/primetime/user-guide.html)。
