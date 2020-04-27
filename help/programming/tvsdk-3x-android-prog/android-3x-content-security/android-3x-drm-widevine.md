---
description: Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションをアドビの統合ソリューションの代わりに使用することもできます。
seo-description: Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションをアドビの統合ソリューションの代わりに使用することもできます。
seo-title: Widevine DRM
title: Widevine DRM
uuid: 3a5fd786-4319-4e92-83b6-0f5328df6a44
translation-type: tm+mt
source-git-commit: ddcdf38fb7a77b7609a21bbdf6b32188b917e22c

---


# Widevine DRM {#widevine-drm}

Primetime Digital Rights Management(DRM)システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティのDRMソリューションをアドビの統合ソリューションの代わりに使用することもできます。

サードパーティのDRMソリューションの可用性に関する最新情報については、アドビの担当者にお問い合わせください。

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

HLS CMAFストリームでAndroidネイティブWidevine DRMを使用できます。

>[!NOTE]
>
> Widevine CENC CTRスキームには、Androidバージョン4.4（APIレベル19）以上が必要です。
>
> Widevine CBCSスキームには、Androidバージョン7.1（APIレベル25）以上が必要です。

## ライセンスサーバーの詳細の設定 {#license-server-details}

MediaPlayerリソースを読み込む前に、 `com.adobe.mediacore.drm.DRMManager` 次のAPIを呼び出します。

```java
public static void setProtectionData(
String drm,
String licenseServerURL,
Map<String, String> requestProperties)
```

### 引数 {#arguments-license-server}

* `drm`  — ウィデ `"com.widevine.alpha"` ビンに。

* `licenseServerURL`  — ライセンス要求を受け取るWidevineライセンスサーバーのURL。

* `requestProperties`  — 発信ライセンス要求に含める追加のヘッダーが含まれます。

例えば、Expressplay DRM用にパッケージ化されたコンテンツを使用する場合、再生する前に次のコードを使用します。

```java
DRMManager.setProtectionData(
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null);
```

## カスタムコールバックの提供 {#custom-callback}

MediaPlayerリソースを読み込む前に、 `com.adobe.mediacore.drm.DRMManager` 次のAPIを呼び出します。

```java
public static void setMediaDrmCallback(
MediaDrmCallback callback)
```

### 引数 {#arguments-custom-callback}

* `callback`  — デフォルトの代わりに使用するMediaDrmCallbackのカスタム実装 `com.adobe.mediacore.drm.WidevineMediaDrmCallback`。

詳しくは、3.11 APIリファレンスを参照してください。

## 現在読み込まれているMediaPlayerリソースのPSSHボックスを取得 {#pssh-box-mediaplayer-resoource}

次の `com.adobe.mediacore.drm.DRMManager` APIを呼び出します。できれば、カスタムコールバック実装で呼び出します。

```java
public static byte[] getPSSH()
```

APIは、読み込まれたWidevineメディアリソースに関連付けられた保護システム固有のヘッダーボックスを返します。

有効なボックスは、短い間（DRMインスタンスの作成とキーの読み込みの間）使用できます。 `MediaDrmCallback callback executeKeyRequest()` を使用して、ライセンスキーの取得をカスタマイズできます。

>[!NOTE]
>
> `getPSSH()` APIは、単一のプレーヤーインスタンスでのみサポートされます。 複数のプレーヤーまたはインスタントオン機能は、正しいボックスを受け取るために、シリアルに初期化する必要があります。
