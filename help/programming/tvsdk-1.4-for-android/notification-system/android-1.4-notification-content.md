---
description: MediaPlayerNotificationオブジェクトは、プレイヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止させるエラーは、プレイヤーの状態が変化する原因にもなります。
seo-description: MediaPlayerNotificationオブジェクトは、プレイヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止させるエラーは、プレイヤーの状態が変化する原因にもなります。
seo-title: 通知内容
title: 通知内容
uuid: 89fb8f63-b0d5-45cd-bdad-348529fd07d0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---


# 通知内容{#notification-content}

MediaPlayerNotificationオブジェクトは、プレイヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止させるエラーは、プレイヤーの状態が変化する原因にもなります。

アプリケーションは、通知と状態情報を取得できます。 通知情報を使用して、診断と検証のログシステムを作成することもできます。

イベントリスナーを実装して、イベントを取得し、応答します。 多くのイベントは`MediaPlayerNotification`ステータス通知を提供します。

`MediaPlayerNotification` プレイヤーのステータスに関連する情報を提供します。

TVSDKは、`MediaPlayerNotification`通知の時系列リストを提供します。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * `type`:INFO、WARNまたはERROR。
   * `code`:通知の数値表現。
   * `name`:SEEK_ERRORなど、通知の解読可能な説明
   * `metadata`:通知に関する関連情報を含むキー/値のペア。例えば、`URL`という名前のキーは、通知に関連するURLの値を提供します。

   * `innerNotification`:この通知に直接影響を与える別の `MediaPlayerNotification` オブジェクトへの参照です。

この情報は、後で分析するためにローカルに保存したり、ログ記録やグラフィカル表現のためにリモートサーバーに送信したりできます。

## 通知システムのセットアップ{#set-up-your-notification-system}

通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。

Primetime Player通知システムの中核は`Notification`クラスで、スタンドアロン通知を表します。

`NotificationHistory`クラスは、通知を蓄積するメカニズムを提供します。 このクラスは、通知のコレクションを表す通知(NotificationHistoryItem)オブジェクトのログを保存します。

通知を受信するには：

* 通知をリッスンする
* 追加通知履歴への通知

1. 状態の変更をリッスンします。
1. `MediaPlayer.PlaybackEventListener.onStateChanged`コールバックを実装します。
1. TVSDKは、2つのパラメーターをこのコールバックに渡します。

   * 新しい状態(`MediaPlayer.PlayerState`)
   * `MediaPlayerNotification`オブジェクト

## 追加リアルタイムログおよびデバッグ{#add-real-time-logging-and-debugging}

通知を使用して、ビデオアプリケーションにリアルタイムログを実装できます。

通知システムを使用すると、システムに過度の負荷をかけることなく、診断と検証のログおよびデバッグ情報を収集できます。

>[!IMPORTANT]
>
>ログバックエンドは、実稼働環境の設定には含まれず、高負荷トラフィックを処理する必要はありません。 完全に導入する必要がない場合は、システムの過負荷を防ぐため、データ送信の効率性を考慮してください。

通知の取得方法の例を次に示します。

1. TVSDK通知システムによって収集されるデータを定期的にクエリするビデオアプリケーション用に、タイマーベースの実行スレッドを作成します。

1. タイマーの間隔が長すぎて、イベントリストのサイズが小さすぎる場合、通知イベントリストがオーバーフローします。 このオーバーフローを回避するには、次のいずれかの操作を行います。

   * スレッドで、新しいイベントのポーリングを行う間隔を短くします。
   * 通知リストのサイズを大きくします。

1. 最新の通知イベントエントリをJSON形式でシリアル化し、後処理のためにリモートサーバーに送信します。

   リモート・サーバは、提供されたデータを視覚的にリアルタイムに表示できます。
1. 通知イベントの消失を検出するには、イベントインデックス値の順序にずれがないかを調べます。

   各通知イベントにはインデックス値があり、`session.NotificationHistory`クラスによって自動的に増分されます。

## ID3タグ{#id-tags}

ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 TVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 アプリケーションは、タグからデータを抽出できます。

>[!IMPORTANT]
>
>TVSDKは、可能なエンコーディング（ASCII、UTF8、UTF16-BEまたはUTF16-LE）のいずれかで、オーディオ(AAC)およびビデオ(H.264)ストリームのID3メタデータ（バージョン2.3.0または2.4.0）を認識します。 認識されるバージョンまたは形式に含まれないID3タグは無視されます。 未指定のエンコーディングはUTF8として扱われます。

TVSDKは、ID3メタデータを検出すると、次のデータを含む通知を発行します。

* InfoCode = 303007
* TYPE = ID3
* NAME =存在しません
* ID = 0

1. `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)`のイベントリスナーを実装し、`MediaPlayer`オブジェクトに登録します。

   TVSDKは、ID3メタデータを検出すると、このリスナーを呼び出します。

   >[!NOTE]
   >
   >カスタム広告キューは、同じ`onTimedMetadata`イベントを使用して、新しいタグの検出を示します。 カスタム広告キューはマニフェストレベルで検出され、ID3タグはストリームに埋め込まれるので、混乱の原因になりません。 詳しくは、custom-tags-configureを参照してください。

1. メタデータを取得します。

   ```java
   @Override 
   public void onTimedMetadata(TimedMetadata timedMetadata) { 
       TimedMetadata.Type type = timedMetadata.getType(); 
       if (type.equals(TimedMetadata.Type.ID3)){ 
           long time = timeMetadata.getTime(); 
           Metadata metadata = timedMetadata.getMetadata(); 
           Set<String> keys = metadata.keySet(); 
           for (String key : keys){ 
               String value = metadata.getValue(key); 
           } 
       } 
   }
   ```
