---
description: TVSDKは、Adobe Primetimead decisioningなどの広告配信サービスと通信し、その広告のビデオストリームに対応するプライマリプレイリストファイルを取得しようとします。 広告解決フェーズ中に、TVSDKはリモート広告配信サーバーに対してHTTP呼び出しを行い、サーバーの応答を解析します。
title: 広告解決フェーズ
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---


# 広告解決フェーズ{#ad-resolving-phase}

TVSDKは、Adobe Primetimead decisioningなどの広告配信サービスと通信し、その広告のビデオストリームに対応するプライマリプレイリストファイルを取得しようとします。 広告解決フェーズ中に、TVSDKはリモート広告配信サーバーに対してHTTP呼び出しを行い、サーバーの応答を解析します。

TVSDKは、次のタイプの広告プロバイダーをサポートしています。

* メタデータ広告プロバイダー

   広告データはプレーンテキストのJSONファイルにエンコードされます。
* Primetime ad decisioning広告プロバイダー

   TVSDKは、一連のターゲティングパラメーターとアセットID番号を含むリクエストをPrimetime ad decisioningバックエンドサーバーに送信します。 Primetime ad decisioningは、必要な広告情報を含むSMIL(synchronized multimedia integration language)ドキュメントを応答します。
* カスタム広告マーカープロバイダー

   広告がサーバ側からストリームに送り込まれる状況を処理します。 TVSDKは、実際の広告挿入を実行しませんが、サーバー側で挿入された広告を追跡する必要があります。 このプロバイダーは、TVSDKが広告トラッキングの実行に使用する広告マーカーを設定します。

このフェーズでは、次のいずれかのフェイルオーバー状況が発生する可能性があります。

* 接続不足や、リソースが見つからないなどのサーバー側のエラーなどの理由で、データを取得できません。
* データを取得しましたが、形式が無効です。

   これは、例えば、受信データの解析に失敗した場合に発生する可能性があります。

TVSDKは、エラーに関する警告通知を発行し、処理を続行します。
