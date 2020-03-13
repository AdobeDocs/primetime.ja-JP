---
description: コンテンツを再生できない場合があります。 ブラウザーのネットワークスタック、トランスポートレイヤー、オペレーティングシステム、Flash Playerランタイム、Primetime DRMシステムのエラーなど、様々な状況でこの問題が発生する可能性があります。
seo-description: コンテンツを再生できない場合があります。 ブラウザーのネットワークスタック、トランスポートレイヤー、オペレーティングシステム、Flash Playerランタイム、Primetime DRMシステムのエラーなど、様々な状況でこの問題が発生する可能性があります。
seo-title: エラーのトリアグの概要
title: エラーのトリアグの概要
uuid: 44b4ab0e-5f08-44b0-bcb5-a869f6add69b
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# エラーのトリアグ {#triaging-errors}

コンテンツを再生できない場合があります。 ブラウザーのネットワークスタック、トランスポートレイヤー、オペレーティングシステム、Flash Playerランタイム、Primetime DRMシステムのエラーなど、様々な状況でこの問題が発生する可能性があります。

最初の診断手順は、DRM暗号化が数式に導入されない状態で問題が発生するかどうかを判断することです。 コンテンツのパッケージ化を試みますが、コンテンツを暗号化しないようにパッケージャーに指示します。 問題が解決しない場合は、コンテンツのエンコードやパッケージ化、またはネットワークインフラストラクチャのどこかで問題が発生する可能性があります。 コンテンツを暗号化せずにパッケージ化すると問題が解消する場合、再生の失敗はDRMの問題が原因の可能性が高いので、クライアント/サーバーのトリエージングに取り組む必要があります。

Primetime DRM（Primetime Cloud DRM以外）は、数年間市場に出回っています。 そのため、Primetime DRMのトラブルシューティングと設定に関するコミュニティの情報は豊富です。 アドビは、Primetime DRM（旧称Adobe Access）ユーザーが問題と解決を集約し、共有するためのフォーラムを提供しています。 お客様の問題が既に話し合われているかどうかを判断するには、以下を確認してください。https://forums.adobe.com/community/adobe_access [](https://forums.adobe.com/community/adobe_access)

## クライアントエラーのトリアリング {#section_D0EBAEB0C27F4B01BD44124DEE62F6BA}

コンテンツが再生されない場合は、サンプルビデオプレーヤーの右側のパネルを確認してください。このパネルで発生したすべての情報が記録 `DRMErrorEvent` されます。 エラーイベントがある場合、Flash Playerランタイムエラーの1つに関連付けられます。

* [DRM Client Error Message Reference](https://help.adobe.com/en_US/primetime/drm/index.html#reference-DRM_Client_Error_Messages);または
* [AS3 Flash Runtime Errors](https://help.adobe.com/en_US/FlashPlatform/reference/actionscript/3/runtimeErrors.html) （DRMの問題は3300から始まります）

