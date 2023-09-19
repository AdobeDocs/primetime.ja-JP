---
description: フォールバックルールが有効になっているデジタルビデオ広告配信テンプレート (VAST) 広告（またはクリエイティブ）の場合、 TVSDK は無効なメディアタイプの広告を空の広告として扱い、その代わりにフォールバック広告を使用しようとします。 フォールバック動作のいくつかの側面を設定できます。
keywords: ゼロ長の広告；空の広告
title: VAST および VMAP 広告の広告フォールバック
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# 概要 {#ad-fallback-for-vast-and-vmap-ads-overview}

フォールバックルールが有効になっているデジタルビデオ広告配信テンプレート (VAST) 広告（またはクリエイティブ）の場合、 TVSDK は無効なメディアタイプの広告を空の広告として扱い、その代わりにフォールバック広告を使用しようとします。 フォールバック動作のいくつかの側面を設定できます。

VAST/Digital Video Multiple Ad Playlist(VMAP) の仕様では、VAST フォールバックが有効になっている広告の場合、空の広告は自動的にフォールバック広告の使用をトリガーすることを規定しています。 VAST 広告が空の場合、 TVSDK はフォールバック広告の中で、有効な HLS メディアタイプの置換を探します。 ラッパー内の VAST 広告のメディアタイプが無効な場合、 TVSDK はこの広告を空として扱います。 VMAP 内のインライン広告に対して、 TVSDK が同じ処理を行うかどうかを設定できます。 VAST の詳細 `fallbackOnNoAd` 機能： [デジタルビデオ広告サービングテンプレート (VAST)3.0](https://www.iab.net/guidelines/508676/digitalvideo/vsuite/vast).

>[!NOTE]
>
>**長さ 0 の広告** - TVSDK は、時間がゼロの広告を含む VAST 応答、または広告のない広告時間を検出した場合、それらの長さ 0 の広告時間に対して AD_BREAK_START / AD_BREAK_COMPLETE イベントを発生させます。 *この動作は、VOD ストリームにのみ適用されます。* TVSDK は、アプリが SKIP 広告ポリシーを使用している場合でも、これらのイベントを実行します。
>
>TVSDK が実行する処理 *not* ライブストリームに対して AD_BREAK_START / AD_BREAK_COMPLETE イベントを発生させるか、ユーザーが trickplay または seek を使用して長さ 0 の広告を超える広告を探す場合に発生します。
