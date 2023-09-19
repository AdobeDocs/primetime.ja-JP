---
description: TVSDK は、広告サーバー応答で壊れた VMAP を検出すると、1109(NETWORK_AD_URL_FAILED) エラーをディスパッチします。
keywords: 1109;NETWORK_AD_URL_FAILED;VMAP の破損
title: 壊れた VMAP に対するクライアントエラー処理
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# 壊れた VMAP に対するクライアントエラー処理 {#client-error-handling-for-broken-vmap}

TVSDK は、広告サーバー応答で壊れた VMAP を検出すると、1109(NETWORK_AD_URL_FAILED) エラーをディスパッチします。

広告サーバー応答の性質と、広告の読み込み設定に応じて、TVSDK が広告サーバー応答で壊れた VMAP を検出した場合に、プレーヤーが異なる数の 1109 エラーを受け取る可能性があります。

広告サーバーの応答が VMAP XML を指すシナリオを考えてみましょう。 また、広告サーバーの応答に 4 つの使用可能な広告スロットがあり、それぞれが同じ VMAP を指すとします。 最後に、この VMAP が壊れたとします。

このシナリオでは、遅延広告解決が有効な場合 ( [遅延広告解決を有効にする](../../../tvsdk-2.7-for-android/ad-insertion/c-psdk-android-2.7-lazy-ad-resolving/t-psdk-android-2.7-enable-lazy-ad-resolving.md)) の場合、 TVSDK は 2 つの 1109 エラーをディスパッチします（予期されたエラーとは異なります）。1 つのエラーが、タイムラインを介する解析パスのたびにディスパッチされます。 これは、遅延広告解決が有効な場合、 TVSDK は 2 パスで広告を解析するからです。最初のパスはプリロール広告のコンテンツ再生開始の直前に発生し、2 番目のパスは再生開始の後に発生します（ミッドロール広告とポストロール広告）。

>[!NOTE]
>
>このシナリオで、遅延広告解決を無効にした場合、 TVSDK は 1109 エラー（1 つの解析パスのみ）のみを発生させます。
