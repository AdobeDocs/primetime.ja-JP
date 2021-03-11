---
description: クリエイティブの再パッケージ化サービス(CRS)は、HLS以外の広告クリエイティブをHLSストリームで正しく再生できるようにします。 マニフェストサーバーは、非HLS広告に遭遇すると、CRSで呼び出します。
title: CRSの概要
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# CRS {#overview-of-crs}の概要

クリエイティブの再パッケージ化サービス(CRS)は、HLS以外の広告クリエイティブをHLSストリームで正しく再生できるようにします。 マニフェストサーバーは、非HLS広告に遭遇すると、CRSで呼び出します。

>[!NOTE]
>
>デフォルトでは、CRSは無効になっています。 アカウントでCRSを有効にするには、Adobeのテクニカルアカウントマネージャーにお問い合わせください。
>
>TVSDKアプリ内でCRSを有効にする方法について詳しくは、使用しているプラットフォーム向けプログラマーガイドの「TVSDKアプリケーションでCRSを有効にする&#x200B;*」トピックを参照してください。*&#x200B;例えば、Android 3.4の場合は、[TVSDKアプリケーションでのCRSの有効化](../../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-transcoding/android-3x-ad-transcoding.md)を参照してください。

CRSは、コンテンツストリームに対してHTTP Live Streaming(HLS)広告クリエイティブを準備し、クライアント側の広告トラッキング用にID3パケットを挿入します。 サードパーティの広告サーバー、広告ネットワークおよびエージェンシーサーバーから受信したMP4、FLVおよびWebMファイルをHLS形式にトランスコードします。

Adobe Primetime広告挿入は、HLS以外の広告クリエイティブを検出すると、再パッケージ化のためにCRSに送信します。これは通常、3分以内です。 CRSは、トランスコードされた広告クリエイティブを将来の使用のためにCDNサーバーに送信します。 これは&#x200B;**`just-in-time (JIT) repackaging`**&#x200B;と呼ばれます。 また、[再パッケージ化API](../../primetime-ad-insertion/~old-creative-repackaging-service/api-repackage.md)を使用して、広告クリエイティブを必要になる前にトランスコードすることもできます。 これは&#x200B;*`asynchronous repackaging`*&#x200B;と呼ばれます。

また、Adobeに適した別の動作がある場合は、アプリケーションのテクニカルアカウントマネージャがCRSのデフォルト動作を変更することもできます。 以下に例を示します。

* 広告クリエイティブ形式の優先順位。

   VAST/VMAP応答の`MediaFiles`セクションには、異なる`MediaFile`タイプのクリエイティブを含めることができます。 マニフェストサーバーは、デフォルトで、固定された優先順位のセット(`application/x-mpegURL`、`application/vnd.apple.mpegURL`、`video/mp4`、`video/x-flv,video/webm`)に従って1つを選択します。 Adobeは、アカウントの優先度を変更できます。
* 広告のターゲット時間。

   マニフェストサーバーは、コンテンツプレイリストからターゲット広告の長さを検出し、CRSに送信します。 Adobeは、この動作を変更して、CRSがアカウントに指定した固定期間を常に使用するようにできます。
