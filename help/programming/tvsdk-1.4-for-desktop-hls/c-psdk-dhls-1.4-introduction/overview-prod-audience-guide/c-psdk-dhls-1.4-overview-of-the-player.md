---
description: 'TVSDK for Desktop HLSは、様々な機能を備え、次の主な機能を提供します '
seo-description: 'TVSDK for Desktop HLSは、様々な機能を備え、次の主な機能を提供します '
seo-title: Primetime TVSDKの機能
title: Primetime TVSDKの機能
uuid: 0a7ebb05-7da5-49ff-928a-4d2124eaa115
translation-type: tm+mt
source-git-commit: 25a0dfef12ecf10ba939500c4ba539468c41ee1b
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Primetime TVSDKの機能{#primetime-tvsdk-features}

TVSDK for Desktop HLSは、様々な機能を備え、次の主な機能を提供します。

* VODおよびライブ/リニア再生

   * 再生、停止、一時停止、シーク、再生ヘッド位置の取得を行うメソッドを含む、再生ウィンドウの管理。
   * アクセシビリティを向上させるためのクローズドキャプション(608、708、WebVTT)およびオーディオの代替形式
   * キャプションのテキストスタイル設定の制御
   * DVR機能、早送り/巻き戻し（トリック再生モード）
   * ライブコンテンツとVODコンテンツの両方のトリック再生
   * 可変ビットレート(ABR)ロジックとABRコントロールの初期設定
   * ライブマニフェストフェイルオーバーのサポート
   * 調整可能な再生バッファー
   * 302リダイレクトの最適化
   * フラグメントの長さ、サイズ、ダウンロード時間の追跡のサポート

* 広告

   * VPAID 2.0
   * クライアント側での広告の切り替え

      * VAST/VMAPのサポートを含む、シームレスな広告挿入
      * 広告のカスタムキュータグのサポート
      * C3広告のマーキング、置換、削除のサポート
      * ブラックアウトシグナリングを含む、カスタマイズ可能なコンテンツ/広告挿入ワークフロー

* コンテンツの保護

   * デジタル著作権管理(DRM)関連サービスへのアクセス
   * 非暗号化またはProtected HTTP Live Streaming(PHLS)を使用したHLSストリームの再生
   * DRMポリシーに基づく解決ベースの出力制御
   * セッションcookieとメディア認証cookieのサポート
   * 複数ドメインのトークンのパッケージ化

* ビデオおよび広告の追跡

   * QoSイベントトラッキング
   * TVSDKとアプリケーションが、ビデオ、広告、その他の要素の状態に関して非同期に通信するのに役立ち、またログアクティビティに関する通知。
   * Adobe Analyticsとの統合とハートビートのサポート

* ログ

   * デバッグログ。
   * フラグメントの長さ、サイズ、ダウンロード時間の追跡がサポートされます。