---
description: フォールバックルールが有効になっているデジタルビデオ広告配信テンプレート (VAST) 広告（またはクリエイティブ）の場合、 TVSDK は無効なメディアタイプの広告を空の広告として扱い、その代わりにフォールバック広告を使用しようとします。 フォールバック動作のいくつかの側面を設定できます。
title: VAST および VMAP 広告の広告フォールバック
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---

# VAST および VMAP 広告の広告フォールバック {#ad-fallback-for-vast-and-vmap-ads}

フォールバックルールが有効になっているデジタルビデオ広告配信テンプレート (VAST) 広告（またはクリエイティブ）の場合、 TVSDK は無効なメディアタイプの広告を空の広告として扱い、その代わりにフォールバック広告を使用しようとします。 フォールバック動作のいくつかの側面を設定できます。

VAST/Digital Video Multiple Ad Playlist(VMAP) の仕様では、VAST フォールバックが有効になっている広告に対して、空の広告は、フォールバック広告の使用を自動的にトリガーするように指定しています。 VAST 広告が空の場合、 TVSDK はフォールバック広告の中で、有効な HLS メディアタイプの置換を探します。 ラッパー内の VAST 広告のメディアタイプが無効な場合、 TVSDK はこの広告を空として扱います。 VMAP 内のインライン広告に対して、 TVSDK が同じ処理を行うかどうかを設定できます。 VAST の詳細 `fallbackOnNoAd` 機能： [デジタルビデオ広告サービングテンプレート (VAST)3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

## VMAP インライン広告のフォールバック広告動作の定義 {#section_D90BB3C6E539472EABF000C0F616DBE2}

VMAP インライン広告に無効なメディアタイプが含まれている場合、フォールバックをオンにすることができます。

1. 設定 `FallbackOnInvalidCreativeEnabled` から `YES` リニア/インライン広告のメディアタイプが HLS に対して無効な場合に、VMAP をフォールバックします。

   >[!NOTE]
   >
   >デフォルト値は NO です。 リニア広告が無効なメディアタイプがある、または広告を再パッケージできないために失敗した場合、このフラグを使用すると、Primetime Ad Decisioning は、広告が空の VAST ラッパーであった場合と同じフォールバック動作に従うことができます。

   ```
   PTAuditudeMetadata *adMetadata = [[[PTAuditudeMetadata alloc] init] autorelease]; 
   adMetadata.isFallbackOnInvalidCreativeEnabled = YES;
   ```

## VAST および VMAP に対する広告のフォールバック動作 {#section_5B6716CC49CC4C40964CFE9F122C57A6}

Primetime ad decisioning は、空の、または HLS に対して無効なメディアタイプを持つ VAST 広告（クリエイティブ）を検出した場合、フォールバック広告を評価して、何を返すかを決定します。

TVSDK では、有効なメディアタイプは次のみです。 `application/x-mpegURL` (M3U8)。

スタンドアロンのフォールバック広告がある場合、 Primetime ad decisioning プラグインは、これらの広告を次の順序で調べ、有効なメディアタイプを持つ最初の広告を返します。

1. 再パッケージ化が有効になっている場合、無効なメディアタイプを持つ広告の最初の出現は、他の無効なメディアタイプと同様に扱われます。

   再パッケージ化に失敗した場合、このプロセスは広告の追加発生に適用されます。
1. TVSDK は、有効なフォールバック広告を見つけなかった場合、無効なメディアタイプを持つ元の広告を返します。
1. 元の広告の代わりに有効な MIME タイプを持つフォールバック広告が返された場合、 Primetime ad decisioning は、可能な場合、VAST エラー URL にエラーコード 403 を送信します。
1. フォールバック広告がラッパーで、複数の広告を返す場合、正しいメディアタイプを持つ広告のみが返されます。

>[!IMPORTANT]
>
>この動作は、VAST ラッパーの広告に対して常に有効になります。 VMAP 内のインライン VAST 広告に対しては、この動作はデフォルトで無効になっていますが、アプリケーションで有効にすることができます。
