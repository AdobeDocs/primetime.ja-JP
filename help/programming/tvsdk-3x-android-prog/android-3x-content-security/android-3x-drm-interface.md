---
description: Primetime DRM ソリューションの主なクライアント側要素は DRM マネージャーです。 Android SDK に含まれるサンプルアプリケーションには、特定の DRM 操作を実装しやすくするために使用できる DRMHelper クラスも含まれています。
title: Primetime DRM インターフェイスの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Primetime DRM インターフェイスの概要 {#primetime-drm-interface-overview}

Primetime DRM ソリューションの主なクライアント側要素は DRM マネージャーです。 Android SDK に含まれているサンプルアプリケーションには、 `DRMHelper` 特定の DRM 操作を実装しやすくするために使用できるクラス。

<!--<a id="section_4DD54E085AB345FE9BE00865E56B28DB"></a>-->

Primetime DRM は、TVSDK アプリケーションにコンテンツ保護を実装するためのスケーラブルで効率的なワークフローを提供します。 各デジタルメディアファイルのライセンスを作成することで、ビデオコンテンツに対する権限を保護および管理できます。

詳しくは、 TVSDK パッケージに含まれている DRM サンプルプレイヤーコードを参照してください。

DRM を操作するための最も重要な API 要素を次に示します。

* DRM サブシステムを実装する DRM マネージャーオブジェクトへのメディアプレーヤー内の参照。

  ```java
  MediaPlayer.getDRMManager();
  ```

  >[!TIP]
  >
  >この API は有効な `DRMManager` オブジェクトが `MediaPlayerEvent.DRM_METADATA` が起動されます。 を呼び出す場合 `getDRMManager()` このイベントが発生する前に、NULL が返される場合があります。

* The `DRMHelper` ヘルパークラス。DRM ワークフローを実装する際に役立ちます。
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

DRM について詳しくは、 [DRM ドキュメント](https://helpx.adobe.com/primetime/user-guide.html).
