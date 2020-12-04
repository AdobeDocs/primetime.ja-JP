---
seo-title: 乱数の生成
title: 乱数の生成
uuid: 3ea25c48-1dbe-4039-8091-36c289702f78
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---


# 乱数{#generating-random-numbers}を生成しています

十分なエントロピーを確実に生成するために、Linuxサーバでハードウェア乱数ジェネレータを使用できます。 マシンが十分なエントロピーを生成できない場合、`/dev/random`からのデータを待つ間、ランダムなソースを必要とするAdobeアクセス操作はブロックされます。
