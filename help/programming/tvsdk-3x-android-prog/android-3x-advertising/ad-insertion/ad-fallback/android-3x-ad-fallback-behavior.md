---
description: Primetime ad decisioningで、空のVAST広告（クリエイティブ）、またはHLSに対して無効なメディアタイプを持つVAST広告（クリエイティブ）が検出された場合、フォールバック広告を評価して、何を返すかを判断します。
seo-description: Primetime ad decisioningで、空のVAST広告（クリエイティブ）、またはHLSに対して無効なメディアタイプを持つVAST広告（クリエイティブ）が検出された場合、フォールバック広告を評価して、何を返すかを判断します。
seo-title: VASTおよびVMAPの広告のフォールバック動作
title: VASTおよびVMAPの広告のフォールバック動作
uuid: 612416b9-d070-42e2-b68b-74ba52023345
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# VASTおよびVMAPの広告のフォールバック動作 {#ad-fallback-behavior-for-vast-and-vmap}

Primetime ad decisioningで、空のVAST広告（クリエイティブ）、またはHLSに対して無効なメディアタイプを持つVAST広告（クリエイティブ）が検出された場合、フォールバック広告を評価して、何を返すかを判断します。

<!--<a id="section_9F60AF00CE9645848EAAF8C06A9E426B"></a>-->

TVSDKでは、有効なメディアタ `application/x-mpegURL` イプは(M3U8)のみです。

スタンドアロンのフォールバック広告がある場合、Primetime ad decisioningプラグインはこれらの広告を次の順序で調べ、有効なメディアタイプを持つ最初の広告を返します。

1. 再パッケージ化が有効な場合、メディアタイプが無効な広告の最初のオカレンスは、他の無効なメディアタイプと同様に扱われます。

   再パッケージ化に失敗した場合、このプロセスは広告の追加のオカレンスに適用されます。
1. TVSDKは、有効なフォールバック広告を見つけなかった場合、無効なメディアタイプを持つ元の広告を返します。
1. 元の広告の代わりに有効なMIMEタイプを持つフォールバック広告が返されると、Primetime ad decisionは、可能な場合はVASTエラーURLにエラーコード403を送信します。
1. フォールバック広告がラッパーで、複数の広告を返す場合、正しいメディアタイプを持つ広告のみが返されます。

>[!IMPORTANT]
>
>この動作は、VASTラッパーの広告で常に有効です。 VMAP内のインラインのVAST広告の場合、動作はデフォルトで無効になっていますが、アプリケーションで有効にすることができます。