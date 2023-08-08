---
title: 実装モデル
description: 実装モデル
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# 実装モデル {#imp-models}

## サーバー側ポリシー {#ss-policies}

このモデルでは、CM をポリシー決定ポイントとして使用し、アクセスの決定をサービスに委任します。

クライアントは適用されたポリシーを前提としないので、ハートビート応答からの再生中に、セッションの初期化と定期的なベースで、実装で判定を確認する必要があります。
