---
title: 乱数の生成
description: 乱数の生成
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---

# 乱数の生成{#generating-random-numbers}

Linux サーバでハードウェア乱数生成を使用して、十分なエントロピーを確実に生成できます。 マシンが十分なエントロピーを生成できない場合、ランダム性のソースを必要とするAdobeアクセス操作は、からのデータを待つ間にブロックされます。 `/dev/random`.
