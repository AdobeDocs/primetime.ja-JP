---
description: Primetime ad decisioningは、空のVAST広告（クリエイティブ）、またはHLSに対して無効なメディアタイプを持つVAST広告（クリエイティブ）を検出すると、フォールバック広告を評価して、何を返すかを決定します。
title: VASTおよびVMAPに対する広告のフォールバック動作
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 0%

---


# VASTとVMAPに対する広告のフォールバック動作{#ad-fallback-behavior-for-vast-and-vmap}

Primetime ad decisioningは、空のVAST広告（クリエイティブ）、またはHLSに対して無効なメディアタイプを持つVAST広告（クリエイティブ）を検出すると、フォールバック広告を評価して、何を返すかを決定します。

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

TVSDKでは、有効なメディアタイプは`application/x-mpegURL`(M3U8)のみです。

スタンドアロンのフォールバック広告がある場合、Primetime ad decisioningプラグインは、これらの広告を次の順序で調べ、有効なメディアタイプを持つ最初の広告を返します。

1. 再パッケージ化を有効にすると、無効なメディアタイプを持つ広告の最初の出現箇所は、他の無効なメディアタイプと同様に扱われます。

   再パッケージ化に失敗した場合、このプロセスは広告の追加オカレンスに適用されます。
1. TVSDKは、有効なフォールバック広告を見つけなかった場合、無効なメディアタイプを持つ元の広告を返します。
1. 元の広告の代わりに有効なMIMEタイプを持つフォールバック広告が返された場合、可能であれば、Primetime ad decisioningはエラーコード403をVASTエラーURLに送信します。
1. フォールバック広告がラッパーで、複数の広告を返す場合、正しいメディアタイプを持つ広告のみが返されます。

>[!IMPORTANT]
>
>VASTラッパー内の広告に対しては、この動作は常に有効です。 VMAP内のインラインVAST広告の場合、動作はデフォルトで無効になっていますが、アプリケーションで有効にすることはできます。