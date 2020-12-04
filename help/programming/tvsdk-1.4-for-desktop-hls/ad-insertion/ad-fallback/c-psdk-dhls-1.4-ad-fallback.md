---
description: フォールバックルールが有効になっているデジタルビデオ広告サービングテンプレート(VAST)広告（またはクリエイティブ）の場合、TVSDKは、無効なメディアタイプを持つ広告を空として扱い、その場所にフォールバック広告を使用しようとします。 フォールバック動作のいくつかの側面を設定できます。
seo-description: フォールバックルールが有効になっているデジタルビデオ広告サービングテンプレート(VAST)広告（またはクリエイティブ）の場合、TVSDKは、無効なメディアタイプを持つ広告を空として扱い、その場所にフォールバック広告を使用しようとします。 フォールバック動作のいくつかの側面を設定できます。
seo-title: VASTおよびVMAP広告に対する広告のフォールバック
title: VASTおよびVMAP広告に対する広告のフォールバック
uuid: 7b44abf9-50cf-4e39-b594-ceb52208a865
translation-type: tm+mt
source-git-commit: adef0bbd52ba043f625f38db69366c6d873c586d
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 0%

---


# VASTおよびVMAP広告に対する広告のフォールバック{#ad-fallback-for-vast-and-vmap-ads}

フォールバックルールが有効になっているデジタルビデオ広告サービングテンプレート(VAST)広告（またはクリエイティブ）の場合、TVSDKは、無効なメディアタイプを持つ広告を空として扱い、その場所にフォールバック広告を使用しようとします。 フォールバック動作のいくつかの側面を設定できます。

VAST/デジタルビデオ複数広告プレイリスト(VMAP)の仕様では、VASTフォールバックが有効な広告に対して、空の広告は自動的にフォールバック広告の使用をトリガーするとされています。 VAST広告が空の場合、TVSDKはフォールバック広告の中でHLSメディアタイプが有効な置換広告を探します。 ラッパー内のVAST広告のメディアタイプが無効な場合、TVSDKはこの広告を空として扱います。 TVSDKが、VMAP内のインライン広告に対して同じ動作を行うかどうかを設定できます。 VAST `fallbackOnNoAd`機能について詳しくは、[デジタルビデオ広告サービングテンプレート(VAST) 3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast)を参照してください。

Primetime広告挿入バックエンドは、同じVAST/VMAP応答内の異なるメディアタイプから選択できるように、一連の優先順位を維持します。 この優先度リストと変更方法について詳しくは、[CRS](../../../../dynamic-ad-insertion/creative-repackaging-service/crs-overview.md)の概要を参照してください。

## VMAPインライン広告のフォールバック広告動作の定義{#define-fallback-ad-behavior-for-vmap-inline-ads}

VMAPインライン広告に無効なメディアタイプが含まれる場合、フォールバックをオンにできます。

1. `fallbackOnInvalidCreative`をtrueに設定すると、リニア/インライン広告のメディアタイプがHLSに対して無効な場合にVMAPがフォールバックされます。

   デフォルト値はfalseです。 リニア広告が無効なメディアタイプを持つことや、広告を再パッケージできないことが原因でリニア広告が失敗した場合、このフラグを使用すると、Primetime ad decisioningは、広告が空のVASTラッパーであった場合と同じフォールバック動作に従います。

   ```
   var auditudeMetadata:AuditudeSettings = new AuditudeSettings(); 
   auditudeMetadata.fallbackOnInvalidCreative = true;
   ```

## VASTとVMAPに対する広告のフォールバック動作{#ad-fallback-behavior-for-vast-and-vmap}

Primetime ad decisioningは、空のVAST広告（クリエイティブ）、またはHLSに対して無効なメディアタイプを持つVAST広告（クリエイティブ）を検出すると、フォールバック広告を評価して、何を返すかを決定します。

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

TVSDKでは、有効なメディアタイプは`application/x-shockwave-flash`(VPAID)と`application/x-mpegURL`(m3u8)のみです。

スタンドアロンのフォールバック広告がある場合、Primetime ad decisioningプラグインは、これらの広告を次の順序で調べ、有効なメディアタイプを持つ最初の広告を返します。

1. 再パッケージ化を有効にすると、無効なメディアタイプを持つ広告の最初の出現箇所は、他の無効なメディアタイプと同様に扱われます。

   再パッケージ化に失敗した場合、このプロセスは広告の追加オカレンスに適用されます。
1. TVSDKは、有効なフォールバック広告を見つけなかった場合、無効なメディアタイプを持つ元の広告を返します。
1. 元の広告の代わりに有効なMIMEタイプを持つフォールバック広告が返された場合、可能であれば、Primetime ad decisioningはエラーコード403をVASTエラーURLに送信します。
1. フォールバック広告がラッパーで、複数の広告を返す場合、正しいメディアタイプを持つ広告のみが返されます。

>[!IMPORTANT]
>
>VASTラッパー内の広告に対しては、この動作は常に有効です。 VMAP内のインラインVAST広告の場合、動作はデフォルトで無効になっていますが、アプリケーションで有効にすることはできます。