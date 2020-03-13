---
description: MediaPlayerNotificationオブジェクトは、プレイヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーの状態が変化する原因にもなります。
seo-description: MediaPlayerNotificationオブジェクトは、プレイヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーの状態が変化する原因にもなります。
seo-title: 通知内容
title: 通知内容
uuid: 89fb8f63-b0d5-45cd-bdad-348529fd07d0
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 通知内容 {#notification-content}

MediaPlayerNotificationオブジェクトは、プレイヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーの状態が変化する原因にもなります。

アプリケーションは、通知と状態情報を取得できます。 通知情報を使用して、診断と検証のログシステムを作成することもできます。

イベントリスナーを実装して、イベントを取得し、イベントに応答します。 多くのイベントは、ステータス `MediaPlayerNotification` 通知を提供します。

`MediaPlayerNotification` プレイヤーのステータスに関連する情報を提供します。

TVSDKは、通知の時系列のリストを提供 `MediaPlayerNotification` します。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * `type`:INFO、WARNまたはERROR。
   * `code`:通知の数値表現。
   * `name`:SEEK_ERRORなど、通知の解読可能な説明
   * `metadata`:通知に関する関連情報を含むキーと値のペア。 例えば、という名前のキ `URL` ーは、通知に関連するURLの値を提供します。

   * `innerNotification`:この通知に直接影響を与え `MediaPlayerNotification` る別のオブジェクトへの参照です。

この情報は、後で分析するためにローカルに保存したり、ログやグラフィカル表示のためにリモートサーバーに送信したりできます。

## 通知システムの設定 {#set-up-your-notification-system}

通知をリッスンし、独自の通知を通知履歴に追加できます。

Primetime Player通知システムの中核は、スタンドアロン `Notification` 通知を表すクラスです。

クラス `NotificationHistory` は、通知を蓄積するメカニズムを提供します。 通知のコレクションを表す通知(NotificationHistoryItem)オブジェクトのログを保存します。

通知を受信するには：

* 通知のリッスン
* 通知履歴への通知の追加

1. 状態の変更をリッスンします。
1. コールバックを実装 `MediaPlayer.PlaybackEventListener.onStateChanged` します。
1. TVSDKは、2つのパラメーターをコールバックに渡します。

   * 新しい状態( `MediaPlayer.PlayerState`)
   * オブジェクト `MediaPlayerNotification` です。

## リアルタイムログとデバッグの追加 {#add-real-time-logging-and-debugging}

通知を使用して、ビデオアプリケーションにリアルタイムログを実装できます。

通知システムを使用すると、システムに過度の負荷をかけることなく、診断や検証のログおよびデバッグ情報を収集できます。

>[!IMPORTANT]
>
>ログバックエンドは、実稼働環境の設定の一部ではなく、高負荷トラフィックを処理する必要はありません。 実装を完全に完了する必要がない場合は、システムの過負荷を回避するために、データ送信の効率性を考慮します。

通知を取得する方法の例を次に示します。

1. TVSDK通知システムによって収集されたデータを定期的にクエリする、ビデオアプリケーション用のタイマーベースの実行スレッドを作成します。

1. タイマーの間隔が長すぎて、イベントリストのサイズが小さすぎる場合、通知イベントリストはオーバーフローします。 このオーバーフローを回避するには、次のいずれかの操作を行います。

   * 新しいイベントをポーリングするスレッドを駆動する時間間隔を短くします。
   * 通知リストのサイズを大きくします。

1. 最新の通知イベントエントリをJSON形式でシリアル化し、後処理のためにリモートサーバーに送信します。

   リモートサーバーは、提供されたデータをリアルタイムでグラフィカルに表示できます。
1. 通知イベントの損失を検出するには、イベントインデックス値のシーケンス内でギャップを探します。

   各通知イベントにはインデックス値があり、このインデックス値はクラスごとに自動的に増分さ `session.NotificationHistory` れます。

## ID3タグ {#id-tags}

ID3タグは、ファイルのタイトルやアーティスト名など、オーディオファイルやビデオファイルに関する情報を提供します。 TVSDKは、HLSストリーム内のトランスポートストリーム(TS)セグメントレベルでID3タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。

>[!IMPORTANT]
>
>TVSDKは、可能なエンコーディング（ASCII、UTF8、UTF16-BEまたはUTF16-LE）のいずれかで、オーディオ(AAC)ストリームおよびビデオ(H.264)ストリームのID3メタデータ（バージョン2.3.0または2.4.0）を認識します。 認識されるバージョンまたは形式に含まれないID3タグは無視されます。 未指定のエンコーディングはUTF8として扱われます。

TVSDKは、ID3メタデータを検出すると、次のデータを含む通知を発行します。

* InfoCode = 303007
* TYPE = ID3
* NAME =存在しない
* ID = 0

1. のイベントリスナーを実装し `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` 、オブジェクトに登録 `MediaPlayer` します。

   TVSDKは、ID3メタデータを検出すると、このリスナーを呼び出します。

   >[!NOTE]
   >
   >カスタム広告キューは、同じイベントを `onTimedMetadata` 使用して新しいタグの検出を示します。 カスタム広告キューがマニフェストレベルで検出され、ID3タグがストリームに埋め込まれるので、混乱の原因になりません。 詳しくは、custom-tags-configureを参照してください。

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
