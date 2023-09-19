---
title: ロールバック検出
description: ロールバック検出
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '126'
ht-degree: 0%

---

# ロールバック検出 {#rollback-detection}

Adobe・アクセスの実装で、クライアントに状態の維持を要求するビジネス・ルール（再生ウィンドウの間隔など）を使用する場合、Adobeでは、ロールバック・カウンタを追跡し、AIRまたはSWFの許可リストを使用することを強くお勧めします。

ロールバックカウンターは、クライアントからのほとんどの要求でサーバーに送信されます。 Adobe・アクセスの実装にロールバック・カウンタが必要ない場合は、そのカウンタを無視できます。 それ以外の場合、Adobeは、を使用して取得したランダムマシン ID をサーバーに保存することをお勧めします。 `MachineToken.getMachineId().getUniqueId()` — とデータベース内の現在のカウンタ値。 ロールバックカウンターの増分と追跡について詳しくは、 *Adobeアクセス API リファレンス* および *ロールバック検出* in *コンテンツの保護にAdobeアクセス SDK を使用する*.
