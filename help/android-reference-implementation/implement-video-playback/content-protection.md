---
description: Primetimeプレイヤーは、カスタムDRMワークフローとしてPrimetime DRM統合をサポートします。 つまり、ストリームを再生する前に、アプリケーションでDRM認証ワークフローを実装する必要があります。
title: DRMコンテンツの保護
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---


# DRMコンテンツ保護{#drm-content-protection}

Primetimeプレイヤーは、カスタムDRMワークフローとしてPrimetime DRM統合をサポートします。 つまり、ストリームを再生する前に、アプリケーションでDRM認証ワークフローを実装する必要があります。

これを有効にするために、TVSDKは認証用のDRMマネージャーを提供します。 次のワークフローの例は、リファレンスの実装によって示されます。

* Accessコンテンツ保護機能を備えたHLSストリームを読み込んで再生する方法。エラー率が低く、開始が速い環境に最適化されています。
* AES128コンテンツ保護を使用したHLSストリームの読み込みおよび再生方法。
* PHLSコンテンツ保護を備えたHLSストリームを読み込んで再生する方法。エラー率が低く、開始が迅速に向上するように最適化されています。

DRM保護されたすべてのコンテンツは、TVSDKに組み込まれているDRMライブラリによって自動的に処理されます。 ただし、TVSDK APIコールバックを使用して、エラー処理、デバイスの個別化の最適化、ライセンスの取得を公開できます。

## プレイヤー追加に対するコンテンツの保護{#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

再生マネージャーを作成するか、マネージャーファクトリを使用して、プレイヤーにコンテンツ保護を追加できます。

コンテンツ保護マネージャを作成するには：

* DRMシステムを初期化します。

   次のコードの例は、再生開始前にDRMシステムに必要な初期化を確実に開始するために、アプリケーション`onCreate()`関数で`loadDRMServices`を呼び出すことを示しています。

   ```java
   @Override 
    public void onCreate() { 
        super.onCreate();  
        DrmManager.loadDRMServices(getApplicationContext()); 
    }
   ```

* DRMライセンスを事前に読み込みます。

   次のコードの例は、コンテンツリストの読み込みが完了したときに`VideoItems`を読み込むことを示しています。 これにより、DRMライセンスがライセンスサーバーから取得され、ローカルにキャッシュされるので、再生開始が発生した場合に、コンテンツが最小の遅延で読み込まれます。

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
   >設定ユーザーインターフェイスでプリキャッシュDRMライセンスをオンに設定して、コンテンツの読み込み時にDRMライセンスをプリキャッシュすることができます。 ただし、ベストプラクティスは、カタログ内のすべてのライセンスを事前に読み込む代わりに、特定のアイテムを事前に読み込むことです。
   >
   >![](assets/precache-drm-licenses.jpg)

* `ManagerFactory`を使用してDRMエラー処理を実装するには、次のコード行が[!DNL PlayerFragment.java]ファイル内にあることを確認します。

   ```java
   drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
   ```

**関連するAPIドキュメント**

* [DrmManagerクラス](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DrmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)