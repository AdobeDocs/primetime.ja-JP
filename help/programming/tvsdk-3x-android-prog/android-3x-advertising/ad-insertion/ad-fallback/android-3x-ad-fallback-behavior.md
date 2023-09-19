---
description: Primetime ad decisioning で、空の、または HLS に対して無効なメディアタイプを持つ VAST 広告（クリエイティブ）が検出された場合、フォールバック広告を評価して、何を返すかを決定します。
title: VAST および VMAP に対する広告のフォールバック動作
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---

# VAST および VMAP に対する広告のフォールバック動作 {#ad-fallback-behavior-for-vast-and-vmap}

Primetime ad decisioning で、空の、または HLS に対して無効なメディアタイプを持つ VAST 広告（クリエイティブ）が検出された場合、フォールバック広告を評価して、何を返すかを決定します。

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

TVSDK では、有効なメディアタイプは次のみです。 `application/x-mpegURL` (M3U8)。

スタンドアロンのフォールバック広告がある場合、 Primetime ad decisioning プラグインはこれらの広告を次の順序で調べ、有効なメディアタイプを持つ最初の広告を返します。

1. 再パッケージ化が有効になっている場合、無効なメディアタイプを持つ広告の最初の出現は、他の無効なメディアタイプと同様に扱われます。

   再パッケージ化に失敗した場合、このプロセスは広告の追加発生に適用されます。
1. TVSDK は、有効なフォールバック広告を見つけなかった場合、無効なメディアタイプを持つ元の広告を返します。
1. 元の広告の代わりに有効な MIME タイプを持つフォールバック広告が返された場合、 Primetime ad decisioning は、可能な場合、エラーコード 403 を VAST エラー URL に送信します。
1. フォールバック広告がラッパーで、複数の広告を返す場合、正しいメディアタイプを持つ広告のみが返されます。

>[!IMPORTANT]
>
>この動作は、VAST ラッパーの広告に対して常に有効になります。 VMAP 内のインライン VAST 広告に対しては、この動作はデフォルトで無効になっていますが、アプリケーションで有効にすることができます。
