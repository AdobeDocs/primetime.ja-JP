---
seo-title: 同期の要件
title: 同期の要件
uuid: 976a0ae1-bece-437e-b95b-6cd222525d13
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '163'
ht-degree: 0%

---


# 同期の要件{#requirements-for-synchronization}

クライアントがサーバーと状態を同期する頻度を指定します。 クライアントが帯域外ライセンスを発行された場合（ライセンスサーバーに接続されない場合）、クライアントのセキュリティで保護された時間を同期し、クライアントの状態をサーバーに報告するために、クライアントが同期メッセージをサーバーに送信する必要があると、使用ルールが指定されます。

同期動作は、次のパラメーターを使用して定義します。

* 「開始間隔」 — 最後に成功した開始から別の同期要求への同期後の待機時間を指定します。
* 「ハードストップ間隔」(Hard Stop Interval) — （オプション） 指定された時間内に正常な同期が発生しなかった場合は、再生を許可しません。
* 「強制同期の確率」 — （オプション）。 クライアントが次の開始間隔の前に同期メッセージを送信する確率。

>[!NOTE]
>
>この使用ルールは、Adobeアクセスクライアントバージョン3.0以降でサポートされています。 古いクライアントでの動作は、ライセンスサーバーでサポートされている最小クライアントバージョンによって異なります。 「 [最小クライアントバージョン](../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md)」を参照してください。

