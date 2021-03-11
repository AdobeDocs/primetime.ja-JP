---
title: 乱数の生成
description: 乱数の生成
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---


# 乱数{#generating-random-numbers}を生成しています

十分なエントロピーを確実に生成するために、Linuxサーバでハードウェア乱数ジェネレータを使用できます。 マシンが十分なエントロピーを生成できない場合、`/dev/random`からのデータを待つ間、ランダムなソースを必要とするAdobeアクセス操作はブロックされます。
