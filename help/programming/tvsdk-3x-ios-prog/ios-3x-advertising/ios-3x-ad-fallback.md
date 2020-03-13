---
description: フォールバックルールが有効なデジタルビデオ広告サービングテンプレート(VAST)広告（またはクリエイティブ）の場合、TVSDKは、無効なメディアタイプを持つ広告を空の広告として扱い、代わりにフォールバック広告を使用しようとします。 フォールバック動作の一部を設定できます。
seo-description: フォールバックルールが有効なデジタルビデオ広告サービングテンプレート(VAST)広告（またはクリエイティブ）の場合、TVSDKは、無効なメディアタイプを持つ広告を空の広告として扱い、代わりにフォールバック広告を使用しようとします。 フォールバック動作の一部を設定できます。
seo-title: VAST広告とVMAP広告の広告のフォールバック
title: VAST広告とVMAP広告の広告のフォールバック
uuid: ca65f349-012d-49e3-8c23-fd041c5362ee
translation-type: tm+mt
source-git-commit: 557f42cd9a6f356aa99e13386d9e8d65e043a6af

---


# VAST広告とVMAP広告の広告のフォールバック {#ad-fallback-for-vast-and-vmap-ads}

フォールバックルールが有効なデジタルビデオ広告サービングテンプレート(VAST)広告（またはクリエイティブ）の場合、TVSDKは、無効なメディアタイプを持つ広告を空の広告として扱い、代わりにフォールバック広告を使用しようとします。 フォールバック動作の一部を設定できます。

VAST/Digital Video Multiple Ad Playlist(VMAP)の仕様では、VASTフォールバックが有効な広告に対して、空の広告が自動的にフォールバック広告の使用をトリガーするという内容が示されています。 VAST広告が空の場合、TVSDKはフォールバック広告の中で有効なHLSメディアタイプの置き換えを探します。 ラッパー内のVAST広告のメディアタイプが無効な場合、TVSDKはこの広告を空として扱います。 TVSDKがVMAP内のインライン広告に対して同じ処理を行うかどうかを設定できます。 VAST機能について詳しくは、 `fallbackOnNoAd` デジタルビデ [オ広告配信テンプレート(VAST) 3.0を参照してください](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast)。

## VMAPインライン広告のフォールバック広告動作の定義 {#section_D90BB3C6E539472EABF000C0F616DBE2}

VMAPインライン広告に無効なメディアタイプが含まれる場合は、フォールバックをオンにできます。

1. リニア `FallbackOnInvalidCreativeEnabled` /イ `YES` ンライン広告のメディアタイプがHLSに対して無効な場合にVMAPをフォールバックするように設定します。

   >[!NOTE]
   >
   >デフォルト値はNOです。 リニア広告が無効なメディアタイプを持つことや、広告を再パッケージ化できないことが原因でリニア広告が失敗した場合、このフラグにより、Primetime ad decisioningは、広告が空のVASTラッパーであった場合と同じフォールバック動作に従います。

   ```
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.isFallbackOnInvalidCreativeEnabled = YES;
   ```

## VASTおよびVMAPの広告のフォールバック動作 {#section_5B6716CC49CC4C40964CFE9F122C57A6}

Primetime ad decisioningは、空のVAST広告（クリエイティブ）、またはHLSに対して無効なメディアタイプを持つVAST広告（クリエイティブ）を検出すると、フォールバック広告を評価して、何を返すかを決定します。

TVSDKでは、有効なメディアタ `application/x-mpegURL` イプは(M3U8)のみです。

スタンドアロンのフォールバック広告がある場合、Primetime ad decisioningプラグインは、これらの広告を次の順序で調べ、有効なメディアタイプを持つ最初の広告を返します。

1. 再パッケージ化が有効な場合、メディアタイプが無効な広告の最初のオカレンスは、他の無効なメディアタイプと同様に扱われます。

   再パッケージ化に失敗した場合、このプロセスは広告の追加のオカレンスに適用されます。
1. TVSDKは、有効なフォールバック広告を見つけなかった場合、無効なメディアタイプを持つ元の広告を返します。
1. 元の広告の代わりに有効なMIMEタイプを持つフォールバック広告が返された場合、Primetime ad decisioningは、可能な場合はVASTエラーURLにエラーコード403を送信します。
1. フォールバック広告がラッパーで、複数の広告を返す場合、正しいメディアタイプを持つ広告のみが返されます。

>[!IMPORTANT]
>
>この動作は、VASTラッパーの広告で常に有効です。 VMAP内のインラインのVAST広告の場合、動作はデフォルトで無効になっていますが、アプリケーションで有効にすることができます。