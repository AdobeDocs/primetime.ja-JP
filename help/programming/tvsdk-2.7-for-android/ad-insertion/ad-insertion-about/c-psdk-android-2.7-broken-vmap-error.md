---
description: TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。
keywords: 1109;NETWORK_AD_URL_FAILED;broken VMAP
seo-description: TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。
seo-title: 壊れたVMAPのクライアントエラー処理
title: 壊れたVMAPのクライアントエラー処理
uuid: 7cc68c86-bb49-4a1b-a1ec-65ca4c94d75d
translation-type: tm+mt
source-git-commit: 812d04037c3b18f8d8cdd0d18430c686c3eee1ff

---


# 壊れたVMAPのクライアントエラー処理 {#client-error-handling-for-broken-vmap}

TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。

広告サーバーの応答の性質や広告の読み込み設定によっては、TVSDKが広告サーバーの応答で破損したVMAPを検出した場合に、プレイヤーが異なる数の1109エラーを受け取る可能性があります。

広告サーバーの応答がVMAP XMLを指すシナリオを考えてみましょう。 また、広告サーバーの応答に4つの使用可能な広告スロットがあり、それぞれが同じVMAPを指しているとします。 最後に、このVMAPが壊れたとします。

このシナリオでは、遅延広告解決が有効な場合( [Enable lazy ad resolving](../../../tvsdk-2.7-for-android/ad-insertion/c-psdk-android-2.7-lazy-ad-resolving/t-psdk-android-2.7-enable-lazy-ad-resolving.md))、TVSDKは1109エラーを2つ（期待どおりではない）ディスパッチします。タイムライン上の各解析パスで1つのエラーがディスパッチされます。 これは、遅延広告解決が有効な場合、TVSDKは2パスで広告を解析するからです。最初のパスは、コンテンツ再生がプリロール広告の開始直前に発生し、2番目のパスは再生開始後（ミッドロール広告とポストロール広告の場合）に発生します。

>[!NOTE]
>
>このシナリオでは、遅延広告解決を無効にすると、TVSDKは1つの1109エラー（解析パスが1つだけ）のみを発生します。

