---
title: Primetime リリースノート
description: Primetime リリースノート
copied-description: true
exl-id: 29087a3e-f16e-4510-8d3a-ed2229700899
source-git-commit: fe0f5f3399d2e2ab3e07713fbcd29ede47888d98
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 28%

---

# Primetime リリースノート

このたびは、Adobe Primetimeリリースノートをご利用いただき、誠にありがとうございます。 左側のナビゲーションに示すドキュメントには、リリース固有の情報、システム要件、制限事項、修正された問題、既知の問題が記載されています。

## PTAI 21.5.1の機能強化および修正点

このリリースには、今後のダッシュボード変更に関する新しい遠隔測定機能が含まれています。また、SCTEベースのキュー形式に対する非推奨のセグメント化タイプ0x01(UPID)のサポートも含まれています。

その他の修正および詳細については、[Ad Insertionリリースノート](/help/release-notes/ptai-21x-release-notes.md)を参照してください。

## TVSDK 3.13 iOSの機能強化および修正点

このリリースでは、LIVE、VOD、FERストリーム用のDEMUXED「HLS/CMAF」（プリロール、ミッドロール、ポストロール）広告のサポートが導入されています。

その他の修正および詳細については、[TVSDK for iOSリリースノート](../release-notes/tvsdk-3x-ios.md)を参照してください。

## TVSDK 3.13 Androidの修正点

このリリースでは、FireTV 3世代PendantとFire TV Cube 1世代および2世代のデバイスを含むFireTVデバイスのABRスイッチで、Widevine DRMストリームがフリーズしたり黒いフレームが表示されたりする問題を回避できます。

この問題を解決するには、再生を開始する前に、指定したFire TVデバイスのAPI `MediaPlayer.flushVideoDecoderOnHeaderChange(true)`を設定します。 デフォルト値はfalseです。

詳しくは、[TVSDK for Androidのリリースノート](../release-notes/tvsdk-3x-android.md)を参照してください。

## 関連トピック

| ユーザーガイド | 説明 |
|--- |--- |
| [Primetime プログラミングのヘルプ](/help/programming/home.md) | Android デバイスでは Java、iOS デバイスでは Objective-C を使用したアプリケーションやビデオプレーヤーの開発を学習できます。 |
| [Primetimeの移行とコンバージョンのヘルプ](/help/migration-guides/home.md) | 既存の Primetime TVSDK Suite から次世代のスイートに移行するためのコンバージョンと移行のプロセスについて説明します。 |
| [参照実装](/help/android-reference-implementation/home.md) | TVSDK を理解し、機能マネージャーを変更して、個人用プレーヤーをカスタマイズします。 |
| [Primetime APIリファレンス](/help/reference/api-references.md) | TVSDK 関数、データ構造、および他のプログラミング構成に関する詳細な情報を提供します。 |
| [Digital Rights Management](/help/digital-rights-management/home.md) | Digital Rights Management(DRM)の様々なユーザーシナリオの詳細を学ぶのに役立ちます |
| [Primetime Ad Insertion のヘルプ](/help/primetime-ad-insertion/home.md) | ユーザーをターゲットに設定した動的な広告をサーバーに挿入してコンテンツを収益化し、パーソナライズされた広告をオーディエンスに提供する方法について説明します。 |
| [アーカイブ](https://helpx.adobe.com/primetime/archives.html) | アーカイブ済みドキュメントのPDFをダウンロードします。 |

## 参考リソース

* [知るAdobe Primetime](https://www.adobe.com/in/marketing/primetime.html)

* [同時実行性の監視](https://tve.helpdocsonline.com/concurrency-monitoring-introduction)

* [Primetime認証](https://tve.helpdocsonline.com/home)

* [Adobe Primetime DRMフォーラム](https://forums.adobe.com/community/adobe_access)

* [Adobe Primetime開発者向けリソース](https://www.adobe.com/devnet/primetime.html)
