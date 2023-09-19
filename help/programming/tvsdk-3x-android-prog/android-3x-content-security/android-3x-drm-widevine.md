---
description: PrimetimeDigital Rights Management(DRM) システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティの DRM ソリューションを、Adobeの統合ソリューションの代わりに使用することもできます。
title: Widevine DRM
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Widevine DRM {#widevine-drm}

PrimetimeDigital Rights Management(DRM) システムの機能を使用して、ビデオコンテンツへの安全なアクセスを提供できます。 または、サードパーティの DRM ソリューションを、Adobeの統合ソリューションの代わりに使用することもできます。

サードパーティの DRM ソリューションの入手方法に関する最新情報については、Adobe担当者にお問い合わせください。

<!--<a id="section_1385440013EF4A9AA45B6AC98919E662"></a>-->

Android のネイティブ Widevine DRM を HLS CMAF ストリームで使用できます。

>[!NOTE]
>
> Widevine CENC CTR スキームには、Android バージョン 4.4（API レベル 19）以上が必要です。
>
> Widevine CBCS スキームには、Android バージョン 7.1（API レベル 25）以上が必要です。

## ライセンスサーバーの詳細を設定 {#license-server-details}

次の呼び出しをおこないます。 `com.adobe.mediacore.drm.DRMManager` MediaPlayer リソースを読み込む前の API:

```java
public static void setProtectionData(
String drm,
String licenseServerURL,
Map<String, String> requestProperties)
```

### 引数 {#arguments-license-server}

* `drm` - `"com.widevine.alpha"` ウィデビンにとって

* `licenseServerURL`  — ライセンス要求を受け取る Widevine ライセンスサーバーの URL。

* `requestProperties`  — 送信ライセンス要求に含める追加のヘッダーが含まれます。

例えば、Expressplay DRM 用にパッケージ化されたコンテンツを使用する場合は、再生の前に次のコードを使用します。

```java
DRMManager.setProtectionData(
  "com.widevine.alpha",  
  "https://wv.service.expressplay.com/hms/wv/rights/?ExpressPlayToken= 
<i>token</i>",  
  null);
```

## カスタムコールバックの提供 {#custom-callback}

次の呼び出しをおこないます。 `com.adobe.mediacore.drm.DRMManager` MediaPlayer リソースを読み込む前の API。

```java
public static void setMediaDrmCallback(
MediaDrmCallback callback)
```

### 引数 {#arguments-custom-callback}

* `callback`  — デフォルトの代わりに使用する MediaDrmCallback のカスタム実装 `com.adobe.mediacore.drm.WidevineMediaDrmCallback`.

詳しくは、 [Android TVSDK 3.11 API ドキュメント](https://help.adobe.com/en_US/primetime/api/psdk/javadoc3.11/index.html).

## 現在読み込まれている MediaPlayer リソースの PSSH ボックスを取得 {#pssh-box-mediaplayer-resoource}

次の呼び出しをおこないます。 `com.adobe.mediacore.drm.DRMManager` API。できれば、カスタムコールバック実装で使用します。

```java
public static byte[] getPSSH()
```

API は、読み込まれた Widevine メディアリソースに関連付けられた保護システム固有のヘッダーボックスを返します。

有効なボックスは、（DRM インスタンスの作成からキーの読み込みの間に）短時間使用できます。 `MediaDrmCallback callback executeKeyRequest()` を使用して、ライセンスキーを取得するのをカスタマイズできます。

>[!NOTE]
>
> `getPSSH()` API は、単一のプレーヤーインスタンスでのみサポートされます。 複数のプレーヤーまたはインスタントオン機能は、正しいボックスを受け取るために、シリアルに初期化する必要があります。
