---
description: 広告の解決と広告の読み込みにより、ユーザーが再生を開始するのを待つのに許容できない遅延が生じる可能性があります。 遅延広告読み込み機能と遅延広告解決機能は、この起動遅延を減らすことができます。
keywords: 遅延；広告解決；広告読み込み
title: 遅延広告解決
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# 概要 {#lazy-ad-resolving}

広告の解決と広告の読み込みにより、ユーザーが再生を開始するのを待つのに許容できない遅延が生じる可能性があります。 遅延広告読み込み機能と遅延広告解決機能は、この起動遅延を減らすことができます。

* 基本的な広告の解決と読み込みプロセス：

   1. TVSDK は、マニフェスト（プレイリスト）をダウンロードし、 *解決済み* すべての広告。
   1. TVSDK *負荷* すべての広告をタイムラインに配置します。
   1. TVSDK は、プレーヤーを PREPARED ステータスに移動し、コンテンツの再生を開始します。

  プレーヤーは、マニフェスト内の URL を使用して広告コンテンツ（クリエイティブ）を取得し、TVSDK が再生できる形式の広告コンテンツを提供し、 TVSDK が広告をタイムラインに配置します。 広告の解決と読み込みのこの基本的なプロセスにより、特にマニフェストに複数の広告 URL が含まれている場合に、ユーザーがコンテンツの再生を待機するのに許容できない長い時間がかかる可能性があります。

* *遅延広告読み込み*:

   1. TVSDK はプレイリストと *解決済み* すべての広告。
   1. TVSDK *負荷* プリロール広告を使用する場合は、プレーヤーを PREPARED ステータスに移動し、コンテンツの再生が開始されます。
   1. TVSDK *負荷* 残りの広告を追加し、再生が発生するとタイムラインに配置します。

  この機能は、すべての広告が読み込まれる前にプレーヤーを PREPARED ステータスにすることで、基本的なプロセスを改善します。

* *遅延広告解決*:

   1. TVSDK はプレイリストをダウンロードします。
   1. TVSDK は、プリロール広告を解決して読み込み、プレーヤーを PREPARED ステータスに移動させると、コンテンツの再生が開始します。
   1. TVSDK は、残りの広告を解決して読み込み、再生が発生するとタイムラインに配置します。

  遅延広告解決は、遅延広告読み込みに基づいてビルドを解決し、より迅速に起動できるようにします。 TVSDK がプリロール広告を配置した後、プレーヤーを PREPARED ステータスに移動し、追加の広告を解決してタイムラインに配置します。

>[!IMPORTANT]
>
>遅延広告解決で考慮すべき要因：
>
>* 遅延広告解決はデフォルトで有効になっています。 無効にした場合、再生が開始される前に、すべての広告が解決されます。
>* 遅延広告解決は、すべての広告が解決されるまで、シークやトリック再生を許可しません。
>
>    * プレーヤーは、 `kEventAdResolutionComplete` イベントを設定してください。
>    * 広告の解決中にユーザーがシークまたはトリック再生操作を実行しようとすると、 TVSDK は `kECLazyAdResolutionInProgress` エラー。
>    * 必要に応じて、プレーヤーでスクラブバーを更新する必要があります。 *次より後* 受信 `kEventAdResolutionComplete` イベント。
>
>* 遅延広告解決は VOD に対してのみ有効です。 ライブストリームでは機能しません。
>* 遅延広告解決が *即時オン* 機能。
>
>  Instant On について詳しくは、「 Instant-on 」を参照してください。
>
>* 遅延広告解決により再生がはるかに高速に開始されますが、再生の最初の 60 秒で広告の時間が発生した場合は、解決されない可能性があります。
>* 遅延広告解決は、プリロール広告には影響しません。
