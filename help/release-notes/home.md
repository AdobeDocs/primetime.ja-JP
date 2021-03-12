---
title: Primetime リリースノート
description: Primetime リリースノート
copied-description: true
translation-type: tm+mt
source-git-commit: 944bfb0f3bd0050a9d2974a37f4fabddaaac8a93
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 26%

---


# Primetime リリースノート

Adobe Primetimeリリースノートへようこそ。 左側のナビゲーションに表示されるドキュメントは、リリース固有の情報、システム要件、制限事項、修正された問題、既知の問題を提供します。

## TVSDK 3.13 iOSの機能強化および修正点

このリリースでは、LIVE、VODおよびFERストリーム用のDEMUXED &#39;HLS/CMAF&#39;（プリロール、ミッドロールおよびポストロール）広告のサポートが導入されています。

その他の修正点および詳細については、[TVSDK for iOSリリースノート](../release-notes/tvsdk-3x-ios.md)を参照してください

## PTAI 21.2.2の機能強化および修正点

このリリースでは、HLSストリーム内のEXT-X-IMAGE-STREAM-INFストリーム挿入/同期のサポートが含まれています。 この機能は、サーバー側の設定を通じて有効になります。 この機能を有効にするには、テクニカルアカウント担当者にお問い合わせください。

## TVSDK 3.13 Androidの修正点

このリリースでは、FireTV 3世代PendantやFireTVキューブ1世代および2世代のデバイスを含むFireTVデバイスのABRスイッチで、Widevine DRMストリームのフリーズや黒いフレームの表示に関する問題を回避できます。

この問題を解決するには、再生を開始する前に、指定したFire TVデバイスのAPI `MediaPlayer.flushVideoDecoderOnHeaderChange(true)`を設定します。 デフォルト値はfalseです。

詳しくは、[TVSDK for Androidリリースノート](../release-notes/tvsdk-3x-android.md)を参照してください。

## TVSDK 3.12 iOSリリースノートの機能強化および修正点

このリリースでは、お客様の主な問題の解決に重点を置いています。

[iOS](../release-notes/tvsdk-3x-ios.md)の現在のリリースバージョンの詳細については、こちらを参照してください。

## 関連項目

| ユーザーガイド | 説明 |
|--- |--- |
| [Primetime プログラミングのヘルプ](/help/programming/home.md) | Android デバイスでは Java、iOS デバイスでは Objective-C を使用したアプリケーションやビデオプレーヤーの開発を学習できます。 |
| [Primetime移行とコンバージョンのヘルプ](/help/migration-guides/home.md) | 既存の Primetime TVSDK Suite から次世代のスイートに移行するためのコンバージョンと移行のプロセスについて説明します。 |
| [リファレンスの実装](/help/android-reference-implementation/home.md) | TVSDK を理解し、機能マネージャーを変更して、個人用プレーヤーをカスタマイズします。 |
| [Primetime APIリファレンス](/help/reference/api-references.md) | TVSDK 関数、データ構造、および他のプログラミング構成に関する詳細な情報を提供します。 |
| [Digital Rights Management](/help/digital-rights-management/home.md) | Digital Rights Management(DRM)の様々なユーザーシナリオの詳細を学ぶ |
| [Primetime Ad Insertion のヘルプ](/help/primetime-ad-insertion/home.md) | ユーザーをターゲットに設定した動的な広告をサーバーに挿入してコンテンツを収益化し、パーソナライズされた広告をオーディエンスに提供する方法について説明します。 |
| [アーカイブ](https://helpx.adobe.com/primetime/archives.html) | アーカイブされたドキュメントのPDFをダウンロードします。 |

## 役立つリソース

* [Adobe Primetimeを知る](https://www.adobe.com/in/marketing/primetime.html)

* [並行性の監視](https://tve.helpdocsonline.com/concurrency-monitoring-introduction)

* [Primetime認証](https://tve.helpdocsonline.com/home)

* [Adobe PrimetimeDRMフォーラム](https://forums.adobe.com/community/adobe_access)

* [Adobe Primetime開発者向けリソース](https://www.adobe.com/devnet/primetime.html)
