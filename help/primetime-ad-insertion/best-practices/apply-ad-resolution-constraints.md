---
title: 広告解決の制約の適用
description: null
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# 広告解決の制約の適用{#apply-ad-resolution-constraints}

特定の広告プロバイダーの応答が遅くなる場合があり、ビデオの開始アップ時間が長くなる可能性があります。 PrimetimeAd Insertionは、広告リクエストのタイムアウトと広告解決フェーズ全体をサポートしており、これらの低速な広告プロバイダーの影響を制限します。  フォールバック広告は、ダウンストリーム広告プロバイダーの応答が遅すぎる場合にも挿入されます。  詳しくは、BootstrapAPIの[`ptadtimeout`パラメーターを参照してください。](/help/primetime-ad-insertion/technical-reference/bootstrap-api.md)
