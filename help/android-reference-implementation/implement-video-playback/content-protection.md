---
description: Primetime プレーヤーは、カスタム DRM ワークフローとして Primetime DRM 統合をサポートしています。 つまり、ストリームを再生する前に、アプリケーションで DRM 認証ワークフローを実装する必要があります。
title: DRM コンテンツの保護
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# DRM コンテンツの保護 {#drm-content-protection}

Primetime プレーヤーは、カスタム DRM ワークフローとして Primetime DRM 統合をサポートしています。 つまり、ストリームを再生する前に、アプリケーションで DRM 認証ワークフローを実装する必要があります。

これを有効にするために、 TVSDK は認証用の DRM マネージャーを提供します。 参照実装は、次のワークフローの例を提供します。

* 低エラー率と迅速な起動に最適化された、アクセスコンテンツ保護を使用して HLS ストリームを読み込み、再生する方法。
* AES128 コンテンツ保護を使用して HLS ストリームを読み込み、再生する方法。
* PHLS コンテンツ保護を使用して HLS ストリームを読み込み、再生する方法。エラー率が低く、迅速な起動に最適です。

DRM で保護されたすべてのコンテンツは、TVSDK に組み込まれている DRM ライブラリによって自動的に処理されます。 ただし、 TVSDK API コールバックを使用して、エラー処理、デバイスの個別化の最適化、ライセンスの取得を公開できます。

## プレーヤーへのコンテンツ保護の追加 {#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

再生マネージャーを作成するか、マネージャーファクトリを使用して、プレーヤーにコンテンツ保護を追加できます。

コンテンツ保護マネージャを作成するには：

* DRM システムを初期化します。

  以下のコード例は、 `loadDRMServices` アプリ内 `onCreate()` 関数を使用して、DRM システムに必要な初期化を開始してから再生を開始する必要があります。

  ```java
  @Override 
   public void onCreate() { 
       super.onCreate();  
       DrmManager.loadDRMServices(getApplicationContext()); 
   }
  ```

* DRM ライセンスをプリロードします。

  次のコード例は、 `VideoItems` コンテンツリストの読み込みが完了したとき。 これにより、DRM ライセンスがライセンスサーバーから取得され、ローカルにキャッシュされるので、再生が開始されたときに、コンテンツが最小限の遅延で読み込まれます。

  ```java
  DrmManager.preLoadDrmLicenses(item.getUrl(),  
    new MediaPlayerItemLoader.LoaderListener() { 
  
      @Override 
      public void onLoadComplete(MediaPlayerItem item) { 
          Player.logger.w(LOG_TAG + "::DRMPreload#onLoadComplete", item.getResource().getUrl()); 
      } 
  
      @Override 
      public void onError(MediaErrorCode errorCode, String s) { 
          Player.logger.e(LOG_TAG + "::DRMPreload#onError", s); 
      } 
  } 
  ```

  >[!NOTE]
  >
  >設定ユーザーインターフェイスで、プリキャッシュ DRM ライセンスをオンに設定して、コンテンツの読み込み時に DRM ライセンスをプリキャッシュできます。 ただし、カタログ内のすべてのライセンスを事前に読み込むのではなく、特定の項目を事前に読み込むことをお勧めします。
  >
  >![](assets/precache-drm-licenses.jpg)

* 次を使用するには： `ManagerFactory` DRM エラー処理を実装するには、次のコード行が [!DNL PlayerFragment.java] ファイル：

  ```java
  drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
  ```

**関連する API ドキュメント**

* [クラス DrmManager](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DrmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)
