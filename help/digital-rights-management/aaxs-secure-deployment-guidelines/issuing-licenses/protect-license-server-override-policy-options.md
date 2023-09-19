---
title: ポリシーオプションの上書き
description: ポリシーオプションの上書き
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '89'
ht-degree: 0%

---

# ポリシーオプションの上書き{#overriding-policy-options}

ライセンスを発行する場合、ライセンスサーバーがポリシーで指定された使用規則を上書きできます。 ポリシーで開始日を指定した場合、その開始日より前にライセンスは生成されません。 ただし、ライセンスの生成後に、ライセンスに将来の開始日を設定することはできます。 クライアントは、開始日を回避するためにシステム時間を前に移動するのを防ぐことができないので、このオプションは慎重に使用する必要があります。
