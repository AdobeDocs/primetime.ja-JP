---
description: '次の表に、売上高最適化通知の詳細を示します。 '
seo-description: '次の表に、売上高最適化通知の詳細を示します。 '
seo-title: 売上高最適化コード
title: 売上高最適化コード
translation-type: tm+mt
source-git-commit: 6da7d597503d98875735c54e9a794f8171ad408b
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---


# 売上高最適化コード {#revenue-optimization-code}

次の表に、売上高最適化通知に関する詳細情報を示します。

## 売上高最適化レポートの有効化 {#enable-revenue-optimization-reporting}

このレポートを有効にするには、PTMediaPlayer apiを使用します。 `[mediaPlayersetRevenueOptimizationReportingLevel:PTNotificationTypeInfo]`.

>[!NOTE]
>
>ほとんどの情報通知には、ダウンロードに失敗したリソースのURLなど、関連するメタデータが含まれています。 一部の通知には、問題が発生したのがメインビデオコンテンツ、代替オーディオコンテンツ、広告のどちらであるかを指定するメタデータが含まれています。

|コード |名前 |内部通知 |メタデータキー |コメント |
|—|—|—|—|—|
|401001 | REVENUE_OPTIMIZATION_レポート |なし |異なるイベントに基づくメタデータキーについては、次の表を参照してください。 |なし |

| イベントの詳細 | ContextMetadata |
|---|---|
| **CONTENT_RESOURCE_開始** :MediaPlayer::replaceCurrentResourceが呼び出されると、TVSDKでディスパッチされます。 | clientTimestamp, fallbackOnInvalidCreative, showStaticBanners, hasPreroll,イベント, adSignalingMode, resourceUrl, creativeRepackagingFormat, delayAdLoadingTolerance, zoneID, hasLivePreroll, adLoadingリソースType, creativeRepackagingEnabled, mediaId, clientId |
| **CONTENT_PLAYBACK_開始** ：コンテンツが準備済み状態に入り、再生の準備ができた場合に、TVSDKでディスパッチされます。 このイベントは、すべてのマニフェストのアップロード時にディスパッチされるわけではありません。初回の読み込み時にのみディスパッチされます。 | clientTimestamp、contentURL、contentType、イベント、isLive、clientID |
| **AD_OPPORTUNITY_GENERATED** ：オポチュニティが生成されたときにTVSDKでディスパッチされます。 | clientTimestamp,イベント, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_開始** ：オポチュニティの解決が開始されると、TVSDKでディスパッチされます。 | clientTimestamp,イベント, opportunityId, placementDuration, clientId |
| **AD_OPPORTUNITY_RESOLVE_FAILED** ：広告リゾルバーがMediaPlayerClient::notifyFailed()を呼び出すと、TVSDKでディスパッチされます。 データを入力する必要がある | opportunityId、notificationAD |
| **AD_RESOURCE_LOAD** ：広告リソースがURLで取得された場合にディスパッチされます。 responseStartTime：リクエストが最初に開始された時のUNIXタイムスタンプ。 responseTotalTime：応答の読み込みに要した合計時間（秒）です。 responseStatus：リソースのフェッチ中に発生したステータスコード。 ステータス：「error」または「success」 referrerAdId：このリソースのフェッチを要求した参照元広告id（存在する場合）。 referrerUrl：このリソースの取得を要求した参照URL。 errorMessage：ステータスが「error」の場合、エラーの理由はここにあります。 | opportunityId, resourceType, responseTotalTime, responseStatus, responseStartTime, status, errorMessage, url, referrerURL, referrerAdId |
| **AD_RESOURCE_LOAD_CRS** :CRSがアセットに適用された場合、およびm3u8の応答でディスパッチされます。 resourceType:always &quot;crs&quot;. responseStartTime：リクエストが最初に開始された時のUNIXタイムスタンプ。 responseTotalTime：応答の読み込みに要した合計時間（秒）です。 responseStatus：リソースのフェッチ中に発生したステータスコード。 ステータス：「error」または「success」。 errorMessage：ステータスが「error」の場合、エラーの理由はここにあります。 mediaFileUrl：選択された元のメディアファイルのURL。 mediaFileBitrate：選択されたメディアファイルのビットレート。 mediaFileMimeType:選択されたメディアファイルのMIMEタイプ。 url：最終的なアセットのURL。 | opportunityId、resourceType、responseTotalTime、responseStatus、responseStartTime、status、errorMessage、url、mediaFileURL、mediaFileBitrate、mediaFileMimeType、url |
| **AD_TIMELINE_PLACE** :adBreakがタイムラインに配置された後、TVSDKでディスパッチされます。 このイベントは、広告の時間ごとに1回発生します。 proposedTime：広告の時間が配置されるようにリクエストされた時間。 actualTime：広告の時間が実際に配置された時間。 proposedDuration：挿入用に要求された広告の時間の長さ。 ライブコンテンツの場合は、これがキュー期間になります。 VODコンテンツの場合、通常は —1になります。 actualDuration：挿入される広告の時間の実際の時間。 元のストリームタイムラインで追加または置き換えられた、すべての広告の合計継続時間（各セグメントの継続時間で定義）として計算されます。 proposedAds：提案された広告の時間内の広告の数。 totalAds：正常に配置された広告の数。 広告…n：広告が正常に挿入されると、ここに挿入されます。 広告マニフェスト全体の情報をAD_OPPORTUNITY_RESOLVE_PROCESSから取得できる | opportunityId, status, errorMessage, proposedTime, proposedDuration, actualTime, proposedAds, totalAds, ads_id, ads_type, ads_duration, ads_url |
| **AD_PLAYBACK_開始** ：広告の再生開始後、TVSDKでディスパッチされます。 | clientTimestamp,イベント, id, url, duration, type, opportunityId, clientId |
| **AD_PLAYBACK_COMPLETE** ：広告の再生が完了した後、TVSDKでディスパッチされます。 | clientTimestamp,イベント, id, url, duration, type, opportunityId, clientId |
| **ADBREAK_PLAYBACK_開始** :adbreak開始の再生時にTVSDKでディスパッチされます。 | clientTimestamp,イベント, opportunityId, duration, time, clientId |
| **ADBREAK_PLAYBACK_COMPLETE** :adbreakの再生が完了したときにTVSDKでディスパッチされます。 | clientTimestamp、イベント、opportunityId、clientId |
| **CONTENT_PLAYBACK_COMPLETE** ：コンテンツが完了した場合に、TVSDKでディスパッチされます。これは、ストリームが置換された場合、プレイヤーがエラー状態に入った場合、プレイヤーがリセットされた場合、またはコンテンツが実際に完了した場合に発生します。 このイベントは、sessionIdを追跡するために必要です。 | clientTimestamp,イベント, clientId, url, status, errorMessage |
| **AD_PLAYBACK_ERROR** ：再生中の広告にエラー（バリアントストリームエラー）がある場合にTVSDKでディスパッチされます。 | イベント，エラー，タイムスタンプ， manifestUrl，時間， opportunityId, url |