---
seo-title: 乱数の生成
title: 乱数の生成
uuid: 3ea25c48-1dbe-4039-8091-36c289702f78
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 乱数の生成{#generating-random-numbers}

Linuxサーバでは、十分なエントロピーを確保するために、ハードウェア乱数ジェネレータを使用できます。 マシンが十分なエントロピーを生成できない場合、ランダムのソースを必要とするAdobe Access操作は、からのデータを待つ間にブロックされま `/dev/random`す。
