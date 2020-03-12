---
seo-title: ロールバックの検出
title: ロールバックの検出
uuid: fc80c98f-7ee5-414b-87fe-0dbb8d4f6019
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ロールバックの検出{#rollback-detection}

Adobe Accessの実装で、クライアントが状態（再生ウィンドウの間隔など）を維持する必要があるビジネスルールを使用する場合、サーバーでロールバックカウンターを追跡し、AIRまたはSWFホワイトリストを使用することを強くお勧めします。

rollbackカウンタは、クライアントからのほとんどの要求でサーバに送信されます。 Adobe Accessの実装にロールバックカウンターが不要な場合は、無視できます。 それ以外の場合は、を使用して取得したランダムなマシンIDと、現在のカウン `MachineToken.getMachineId().getUniqueId()`ター値をデータベースに格納することをお勧めします。 ロールバックカウンターの増分と追跡について詳しくは、『 *Adobe Access API Reference* 』の「ClientState」と『 *Rollback detection* 』の「Using the Adobe Access SDK for Protecting *」を参照してください*。
