---
description: Primetimeプレイヤーは、カスタムDRMワークフローとしてPrimetime DRM統合をサポートします。 つまり、ストリームを再生する前に、アプリケーションでDRM認証ワークフローを実装する必要があります。
seo-description: Primetimeプレイヤーは、カスタムDRMワークフローとしてPrimetime DRM統合をサポートします。 つまり、ストリームを再生する前に、アプリケーションでDRM認証ワークフローを実装する必要があります。
seo-title: DRMコンテンツの保護
title: DRMコンテンツの保護
uuid: 95c446f6-8304-4d70-9bef-7368b9364025
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e

---


# DRMコンテンツの保護 {#drm-content-protection}

Primetimeプレイヤーは、カスタムDRMワークフローとしてPrimetime DRM統合をサポートします。 つまり、ストリームを再生する前に、アプリケーションでDRM認証ワークフローを実装する必要があります。

これを有効にするために、TVSDKは認証用のDRMマネージャーを提供します。 参照の実装は、次のワークフローの例を提供します。

* Accessコンテンツ保護機能を使用して、エラー率が低く、クイックスタートアップ用に最適化されたHLSストリームを読み込んで再生する方法。
* AES128コンテンツ保護を使用したHLSストリームの読み込みおよび再生方法。
* PHLSコンテンツ保護を使用して、エラー率が低く、クイックスタートアップ用に最適化されたHLSストリームを読み込んで再生する方法。

DRM保護されたすべてのコンテンツは、TVSDKに組み込まれているDRMライブラリによって自動的に処理されます。 ただし、TVSDK APIコールバックを使用して、エラー処理、デバイスの個別化の最適化、ライセンスの取得を公開できます。

## プレイヤーにコンテンツ保護を追加 {#section_F1FC4322C35C4FE8A3B47FDC0A74221B}

再生マネージャーを作成するか、マネージャーファクトリを使用して、プレイヤーにコンテンツ保護を追加できます。

コンテンツ保護マネージャーを作成するには：

* DRMシステムを初期化します。

   次のコード例は、再生開始前にDRMシ `loadDRMServices` ステムに必要な初期化を確実に開始するた `onCreate()` めに、アプリケーション関数での呼び出しを示しています。

   ```java
   @Override 
    public void onCreate() { 
        super.onCreate();  
        DrmManager.loadDRMServices(getApplicationContext()); 
    }
   ```

* DRMライセンスを事前に読み込みます。

   次のコードの例は、コンテンツリストの読み込みが `VideoItems` 完了したらを読み込む方法を示しています。 これにより、DRMライセンスがライセンスサーバーから取得され、ローカルにキャッシュされ、再生が開始される際に、コンテンツが最小の遅延で読み込まれます。

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
   >コンテンツの読み込み時にDRMライセンスをプリキャッシュするには、設定ユーザーインターフェイスで「プリキャッシュDRMライセンス」を「オン」に設定します。 ただし、ベストプラクティスは、カタログ内のすべてのライセンスを事前に読み込む代わりに、特定の品目を事前に読み込むことです。
   >
   >![](assets/precache-drm-licenses.jpg)

* DRMエラー処 `ManagerFactory` 理を実装するには、次のコード行がファイル内にあることを確認し [!DNL PlayerFragment.java] ます。

   ```java
   drmManager = ManagerFactory.getDrmManager(config, mediaPlayer);
   ```

**関連するAPIドキュメント**

* [DrmManagerクラス](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.html)
* [DrmManagerEventListener](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/manager/DrmManager.DrmManagerEventListener.html)