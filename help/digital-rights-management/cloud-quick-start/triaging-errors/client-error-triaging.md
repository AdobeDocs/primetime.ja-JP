---
description: コンテンツを再生できない場合があります。 ブラウザーのネットワークスタック、トランスポート層、オペレーティングシステム、Flash Playerランタイム、Primetime DRM システムでのエラーなど、様々な状況が原因でこの問題が発生する場合があります。
title: トライジングエラーの概要
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# エラーのトリエージング {#triaging-errors}

コンテンツを再生できない場合があります。 ブラウザーのネットワークスタック、トランスポート層、オペレーティングシステム、Flash Playerランタイム、Primetime DRM システムでのエラーなど、様々な状況が原因でこの問題が発生する場合があります。

最初の診断手順は、式に DRM 暗号化が導入されずに、問題が自身に現れるかどうかを判断することです。 コンテンツをパッケージ化しようとしますが、コンテンツを暗号化しないようにパッケージャに指示します。 問題が解決しない場合は、コンテンツのエンコードやパッケージ、またはネットワークインフラストラクチャ内のどこかで問題が発生する可能性があります。 コンテンツを暗号化せずにパッケージ化すると問題が発生する場合は、DRM の問題が原因で再生に失敗する可能性が高く、クライアント/サーバーのトリエージングに関与する必要があります。

Primetime DRM（Primetime Cloud DRM 以外）は、数年間市場に出回っています。 そのため、Primetime DRM のトラブルシューティングと設定に関するコミュニティソースの情報が豊富に用意されています。 Adobeは、Primetime DRM( 旧称：Adobeアクセス ) ユーザーが問題と解決を集計し共有するためのフォーラムを提供しました。 問題が既に議論されているかどうかを判断するには、次の点を確認してください。 [https://forums.adobe.com/community/adobe_access](https://forums.adobe.com/community/adobe_access)

## クライアントエラーのトリエージング {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}

コンテンツが再生されない場合は、サンプルビデオプレーヤーの右側パネルを調べてください。このパネルには、いずれかのログが記録されます `DRMErrorEvent` それが起こる。 エラーイベントがある場合は、 Runtime ErrorsFlash Playerの 1 つと関連付けられます。

* [DRM クライアントエラーメッセージの参照](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages)；または
* [AS3Flashランタイムエラー](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html) （DRM の問題は 3300 に始まります）
