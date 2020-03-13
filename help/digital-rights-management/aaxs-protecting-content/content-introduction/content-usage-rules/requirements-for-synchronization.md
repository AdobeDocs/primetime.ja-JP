---
seo-title: 同期の要件
title: 同期の要件
uuid: 976a0ae1-bece-437e-b95b-6cd222525d13
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 同期の要件{#requirements-for-synchronization}

クライアントがサーバーと状態を同期する頻度を指定します。 クライアントが（ライセンスサーバーに接続されない状態で）帯域外ライセンスを発行された場合、クライアントの安全な時刻とクライアントの状態をサーバーに報告するために、クライアントが同期メッセージをサーバーに送信する必要があると、使用ルールで指定できます。

同期動作は、次のパラメーターを使用して定義します。

* 開始間隔 — 最後に正常に完了した同期の後に、別の同期要求を開始するまでの待ち時間を指定します。
* ハードストップ間隔 — （オプション）。 指定された時間内に正常に同期が行われなかった場合は再生を許可しない。
* 強制同期の確率 — （オプション）。 クライアントが次の開始間隔の前に同期メッセージを送信する確率。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>この使用ルールは、Adobe Accessクライアントバージョン3.0以降でサポートされています。 古いクライアントでの動作は、ライセンスサーバーでサポートされている最小限のクライアントバージョンによって異なります。 「最小クライアン [トバージョン](../../../aaxs-protecting-content/content-implementing-the-license-server/content-handling-license-reqs/content-minimum-client-version.md)」を参照。

