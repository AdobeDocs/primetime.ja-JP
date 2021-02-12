---
title: ライブ/リニアストリームでのAd Insertionの使用
description: ライブ/リニアストリームでのAd Insertionの使用
translation-type: tm+mt
source-git-commit: 0f98b9848f1764e7c66e3692d8a845513493597f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---


# ライブ/リニアストリームでAd Insertionを使用{#ad-insertion-live-linear-stream}

PrimetimeのAd Insertionにより、発行者は、ライブ/リニアストリーム中に発生する標準的な、複雑な広告挿入状況を処理できます。

## サポートされているキュー形式{#cue-formats-supported}

PrimetimeAd Insertionは、次に示す様々な標準キュー形式と非標準キュー形式をサポートしています。

* DPI SCTE-35（SCTE-35拡張広告マーカー）

* [Adobeデジタルプログラム挿入シグナリング仕様](https://www.adobe.com/content/dam/acom/en/devnet/primetime/PrimetimeDigitalProgramInsertionSignalingSpecification.pdf)

* バイナリSCTE-35（HLSとDASHの両方）

* テキストSCTE-35（HLSとDASHの両方）

その他の詳細やサポートされているキュー形式については、Primetimeのサポート担当者にお問い合わせください。

## 広告ブレークの部分的なサポート{#partial-ad-break-support}

部分的な広告の時間は、広告の時間の開始後にビューアがライブ/リニアストリームに入る状況で使用できます。  例えば、ビューアが1時に2:00の長い広告の時間を入力した場合、広告の時間の一部が挿入され、残りの時間に広告が提供されます。 部分的な広告の時間の挿入がない場合、その時間中は広告はこのビューアに提供されません。 PrimetimeAd Insertionは、適切なタグがメディアストリームに存在する場合、デフォルトで部分的な広告ブレークの挿入を有効にします。

## 早期リターン（早期広告出口） {#early-return-early-ad-exit}

ライブ/リニアストリームの広告の時間から早い段階で返す必要がある場合があります。例えば、スポーツイベントが突然アクションに戻った場合などです。 各ad decisioning形式には、「キューアウト」（広告）または「キューイン」（コンテンツ）へのタグが含まれます。  広告の時間の終了前に「キューイン」タグを検出した場合、Adobe PrimetimeAd Insertionはキューインを受け入れます。  早期返却を有効にするには、コンテンツパッケージャーにお問い合わせください。
