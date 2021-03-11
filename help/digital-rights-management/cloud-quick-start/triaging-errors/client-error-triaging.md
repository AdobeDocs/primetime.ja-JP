---
description: 場合によっては、コンテンツを再生できないことがあります。 ブラウザーネットワークスタック、トランスポートレイヤー、オペレーティングシステム、Flash Playerランタイム、Primetime DRMシステムのエラーなど、様々な状況でこの問題が発生する場合があります。
title: トリエイジングエラーの概要
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---


# エラーのトリエイジング{#triaging-errors}

場合によっては、コンテンツを再生できないことがあります。 ブラウザーネットワークスタック、トランスポートレイヤー、オペレーティングシステム、Flash Playerランタイム、Primetime DRMシステムのエラーなど、様々な状況でこの問題が発生する場合があります。

最初の診断手順は、式にDRM暗号化を導入せずに問題が発生するかどうかを判断することです。 コンテンツをパッケージ化しようとしますが、パッケージャーに対して、コンテンツの暗号化を行わないように指示します。 問題が解決しない場合は、コンテンツのエンコードやパッケージ化、またはネットワークインフラストラクチャのどこかで問題が発生する可能性があります。 コンテンツを暗号化せずにパッケージ化すると問題が解消する場合は、DRMの問題が原因の可能性が高いので、クライアント/サーバーのトリエージングを行う必要があります。

Primetime DRM（Primetime Cloud DRM以外）は、数年間市場に出回っています。 そのため、Primetime DRMのトラブルシューティングと設定に関するコミュニティソースの情報は豊富です。 Adobeは、Primetime DRM(旧称「Adobeアクセス」)ユーザーが集計にアクセスし、問題と解決を共有するためのフォーラムを提供しています。 問題が既に話し合われているかどうかを判断するには、以下を確認してください。[https://forums.adobe.com/community/adobe_access](https://forums.adobe.com/community/adobe_access)

## {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}のトリアリング中にクライアントエラーが発生しました

コンテンツが再生されない場合は、サンプルビデオプレーヤーの右側のパネルを調べてください。このパネルには、発生した`DRMErrorEvent`がすべて記録されます。 エラーイベントがある場合、Flash Playerランタイムエラーの1つに関連付けられます。

* [DRM Client Error Message Reference](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages);または
* [AS3Flashランタイムエラー](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html) (DRMは3300で開始を発行)

