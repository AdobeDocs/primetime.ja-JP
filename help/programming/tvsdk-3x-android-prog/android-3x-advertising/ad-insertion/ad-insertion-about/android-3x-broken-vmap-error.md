---
description: TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。
keywords: 1109;NETWORK_AD_URL_FAILED;broken VMAP
seo-description: TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。
seo-title: 壊れたVMAPのクライアントエラー処理
title: 壊れたVMAPのクライアントエラー処理
uuid: ab2c567d-d945-4ebe-b65a-c1f13518a576
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# 壊れたVMAPのクライアントエラー処理 {#client-error-handling-for-broken-vmap}

TVSDKは、広告サーバーの応答で壊れたVMAPを検出すると、1109(NETWORK_AD_URL_FAILED)エラーをディスパッチします。

広告サーバーの応答の性質や広告の読み込み設定によっては、TVSDKが広告サーバーの応答で破損したVMAPを検出した場合に、プレイヤーが異なる数の1109エラーを受け取る可能性があります。

広告サーバーの応答がVMAP XMLを指すシナリオを考えてみましょう。 また、広告サーバーの応答に4つの使用可能な広告スロットがあり、それぞれが同じVMAPを指しているとします。 最後に、このVMAPが壊れたとします。

このシナリオでは、遅延広告解決が有効な場合(遅延広告解決を有効にする[](../../../../tvsdk-3x-android-prog/android-3x-advertising/ad-insertion/c-lazy-ad-resolving/t-enable-lazy-ad-resolving.md))、TVSDKは1109エラーを2つ（期待どおりではない）ディスパッチします。タイムライン上の各解析パスで1つのエラーがディスパッチされます。 これは、遅延広告解決が有効な場合、TVSDKは2パスで広告を解析するからです。最初のパスは、コンテンツ再生がプリロール広告の開始直前に発生し、2番目のパスは、再生開始後（ミッドロール広告とポストロール広告の場合）に発生します。

>[!NOTE]
>
>このシナリオでは、遅延広告解決を無効にすると、TVSDKは1つの1109エラー（解析パスが1つだけ）のみを発生します。