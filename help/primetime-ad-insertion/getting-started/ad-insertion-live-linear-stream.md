---
title: ライブ/リニアストリームでのAd Insertionの使用
description: ライブ/リニアストリームでのAd Insertionの使用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# ライブ/リニアストリームでのAd Insertionの使用 {#ad-insertion-live-linear-stream}

PrimetimeAd Insertionを使用すると、公開者は、ライブ/リニアストリーム中に発生する標準的で複雑な広告挿入状況を処理できます。

## サポートされるキューの形式 {#cue-formats-supported}

PrimetimeAd Insertionは、次のような様々な標準および非標準のキュー形式をサポートしています。

* DPI SCTE-35 （SCTE-35 拡張広告マーカー）

* [Adobeデジタルプログラム挿入シグナリング仕様](assets/PrimetimeDigitalProgramInsertionSignalingSpecification.pdf)

* バイナリ SCTE-35（HLS と DASH の両方）

* テキスト SCTE-35（HLS と DASH の両方）

その他の詳細やサポートされているキュー形式については、 Primetime サポート担当者にお問い合わせください。

## 部分的な広告ブレークのサポート {#partial-ad-break-support}

部分的な広告の時間は、広告の時間の開始後にビューアがライブ/リニアストリームに入る場合に使用できます。  例えば、ビューアが 1 時に 2:00 の長い広告の時間を入力した場合、部分的な広告の時間挿入により、残りの時間に広告が提供されます。 部分的な広告ブレークの挿入がない場合、ブレーク中にこのビューアに広告が提供されません。 PrimetimeAd Insertionは、メディアストリームに適切なタグが存在する場合、デフォルトで、部分広告ブレーク挿入を有効にします。

## 早期再来訪（早期広告出口） {#early-return-early-ad-exit}

ライブ/リニアストリーム内の広告の時間から早い時間に戻る必要が生じる場合があります。例えば、スポーツイベントが突然行動に戻った場合などです。 各 Ad Decisioning 形式には、「キューアウト」（広告）または「キューイン」（コンテンツ）に対するタグが含まれます。  広告ブレークの終了前に「キューイン」タグが検出された場合、Adobe PrimetimeAd Insertionはキューインを保持します。  早期返品を有効にするには、コンテンツパッケージャーにお問い合わせください。
