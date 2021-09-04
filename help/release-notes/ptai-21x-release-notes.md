---
title: PTAI 21.8.1リリースノート
description: PTAIリリースノートでは、2021年のPrimetimeAd Insertionの新機能と変更点、解決された既知の問題について説明します。
exl-id: 39a05f6d-431a-4416-81b1-21d82c0dbd69
source-git-commit: 97a192ed1d0ddc034f72a836a70293acfcca9881
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# PrimetimeAd Insertion21.8.1のリリースノート

PrimetimeAd Insertion21.x.xのリリースノートでは、2021年のPrimetimeAd Insertionの新機能と変更点、解決された問題、既知の問題について説明します

<!---
Primetime Ad Insertion 21.9.1
When: Tuesday, September 7, 2021 from 02:30 AM to 05:30 AM EASTERN









What:  Primetime Ad Insertion 21.9.1

When:  Tuesday, September 7, 2021 from 02:30 AM to 05:30 AM Eastern Time

Changes:

* Updates to infrastructure components behind PTAI’s mediation and reporting components (Primetime Ads GUI)
-->

## PTAI 21.8.1の新機能

When:2021年8月24日（火）午前2:00 ～ 05:00（東部時間）

* DASHライブ/リニアストリームのサポートが追加されました（VODは既にサポートされています）。

## 以前のリリースバージョンの機能強化および修正点

### バージョン21.5.1

When: 2021年5月26日（水）午前3:30 ～ 06:30（東部時間）

**変更点**

* SCTEベースのキュー形式での非推奨のセグメントタイプ0x01(UPID)のサポートを追加しました。

* 今後のダッシュボードの変更に備えた新しい遠隔測定機能を追加しました。

### バージョン21.4.1

**日時：** 2021年4月22日（木）、午前2:00 ～午前5:00

**変更点**

* セッションリクエスト制限は、潜在的なDDOS攻撃から保護するために有効になります。 セッションは、1秒あたり10個のリクエストに制限され、キューに格納された100個のリクエストの上限になります。 HLS/DASHの仕様に従って動作するプレーヤーへの影響は予想されません。

* その他のメンテナンスおよびセキュリティの強化

### バージョン21.2.2

**日時：** 2021年2月23日（火）午前1時～午前4時（東部時間）

**変更点**

* HLSストリームでのEXT-X-IMAGE-STREAM-INFストリーム挿入/同期のサポートが追加されました。 この機能は、サーバー側の設定を通じて有効になります。 この機能を有効にするには、テクニカルアカウント担当者にお問い合わせください。

### バージョン21.2.1

**日時：** 2021年2月3日（水）午前1:00 ～ 04:00（東部時間）

**変更点**

* DASH出力の最適化のサポートが追加されました。時間ベースのノード統合。

### バージョン21.1.2

**日時：** 2021年1月19日（火）午前12:30 ～ 08:30（東部時間）

**変更点**

* メンテナンスの更新：PrimetimeバックエンドのmemcacheAd Insertionのアップグレード。

### バージョン21.1.1

**日時：** 2021年1月13日（水）午前1時～午前4時（東部時間）

**変更点**

* SCTE35ベースのキュー形式で使用できるアフィリエイトのサポートを追加しました。
