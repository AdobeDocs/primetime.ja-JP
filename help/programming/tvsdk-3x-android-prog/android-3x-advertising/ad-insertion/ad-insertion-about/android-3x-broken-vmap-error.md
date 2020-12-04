---
description: TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。
keywords: 1109;NETWORK_AD_URL_FAILED;broken VMAP
seo-description: TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。
seo-title: 壊れたVMAPのクライアントエラー処理
title: 壊れたVMAPのクライアントエラー処理
uuid: ab2c567d-d945-4ebe-b65a-c1f13518a576
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---


# 壊れたVMAP {#client-error-handling-for-broken-vmap}のクライアントエラー処理

TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。

広告サーバーのレスポンスの性質と、広告の読み込み設定によっては、TVSDKが広告サーバーのレスポンス内で壊れたVMAPに遭遇した場合、プレイヤーは異なる数の1109エラーを受け取る場合があります。

広告サーバーの応答がVMAP XMLを指すシナリオを考えてみましょう。 また、広告サーバーの応答に4つの使用可能な広告スロットがあり、それぞれが同じVMAPを指すとします。 最後に、このVMAPが壊れているとします。

このシナリオでは、遅延広告解決が有効な場合（[遅延広告解決を有効にする](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/t-enable-lazy-ad-resolving.md)）、TVSDKは、2つの1109エラーをディスパッチします（予期したものではありません）。タイムライン上の解析パスごとに1つのエラーがディスパッチされます。 これは、遅延広告解決が有効な場合、TVSDKは2パスで広告を解析するからです。最初のパスは、プリロール広告のコンテンツ再生開始の直前に発生し、2番目のパスは再生開始の後（ミッドロール広告とポストロール広告の後）に発生します。

>[!NOTE]
>
>このシナリオでは、遅延広告解決を無効にすると、TVSDKは1109エラー（解析パスを1つだけ）を1つだけ起動します。