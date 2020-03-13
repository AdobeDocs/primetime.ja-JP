---
description: クリエイティブ再パッケージ化サービス(CRS)を使用すると、HLS以外の広告クリエイティブをHLSストリームで適切に再生できます。 マニフェストサーバーは、HLS以外の広告に遭遇した場合に、CRSで呼び出します。
seo-description: クリエイティブ再パッケージ化サービス(CRS)を使用すると、HLS以外の広告クリエイティブをHLSストリームで適切に再生できます。 マニフェストサーバーは、HLS以外の広告に遭遇した場合に、CRSで呼び出します。
seo-title: CRSの概要
title: CRSの概要
uuid: 3ae75fa7-397f-47ba-8e3d-50543ca25458
translation-type: tm+mt
source-git-commit: 4788a8de8ba47d7f448967066e1bd0fb73fdb7a8

---


# CRSの概要 {#overview-of-crs}

クリエイティブ再パッケージ化サービス(CRS)を使用すると、HLS以外の広告クリエイティブをHLSストリームで適切に再生できます。 マニフェストサーバーは、HLS以外の広告に遭遇した場合に、CRSで呼び出します。

>[!NOTE]
>
>デフォルトでは、CRSは無効です。 アカウントでCRSを有効にするには、アドビのテクニカルアカウントマネージャーにお問い合わせください。
>
>TVSDKアプリ内でCRSを有効にする方法について詳しくは、ご使用のプラットフォームのプログラマーガイドの *CRS in TVSDK* applicationsトピックを参照してください。 例えば、Android 3.4の場合、TVSDKアプリケーションでのCRSの [有効化を参照してください。](../../programming/tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/ad-transcoding/android-3x-ad-transcoding.md)

CRSは、コンテンツストリーム用のHTTP Live Streaming(HLS)広告クリエイティブを準備し、クライアント側の広告トラッキング用にID3パケットを挿入します。 サードパーティの広告サーバー、広告ネットワーク、エージェンシーサーバーから受信したMP4、FLVおよびWebMファイルをHLS形式にトランスコードします。

Adobe Primetimeの広告挿入でHLS以外の広告クリエイティブが検出されると、再パッケージ化のためにCRSに送信されます。通常、この処理には3分以内かかります。 CRSは、トランスコードされた広告クリエイティブをCDNサーバーに送信し、将来使用できるようにします。 これはと呼ばれま **`just-in-time (JIT) repackaging`**&#x200B;す。 また、再パッケージ化APIを使用して、広告クリエイティブを必要になる前にトランスコ [ードできます](../../dynamic-ad-insertion/creative-repackaging-service/api-repackage.md) 。 これはと呼ばれま *`asynchronous repackaging`*&#x200B;す。

また、アドビのテクニカルアカウントマネージャーは、アプリケーションに適した別の動作がある場合、CRSのデフォルト動作を変更することもできます。 次の項目があります。

* 広告クリエイティブの形式の優先順位。

   VAST/VMAP `MediaFiles` 応答のセクションには、異なるタイプのクリエイティブを含めることがで `MediaFile` きます。 マニフェストサーバーは、デフォルトで、固定の優先度のセット(、、、、 `application/x-mpegURL`など `application/vnd.apple.mpegURL`)に従って1つ `video/mp4`を選択しま `video/x-flv,video/webm`す。 アドビは、お客様のアカウントの優先度を変更できます。
* 広告ターゲットの期間。

   マニフェストサーバーは、コンテンツプレイリストからターゲット広告の継続時間を検出し、CRSに送信する。 アドビは、この動作を変更して、CRSが常にアカウントに指定した固定期間を使用するようにできます。
