---
description: MediaPlayerNotification オブジェクトは、プレーヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーの状態が変わる原因にもなります。
title: 通知コンテンツ
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---

# 通知コンテンツ {#notification-content}

MediaPlayerNotification オブジェクトは、プレーヤーの状態、警告およびエラーの変更に関する情報を提供します。 ビデオの再生を停止するエラーは、プレーヤーの状態が変わる原因にもなります。

アプリケーションは、通知と状態の情報を取得できます。 通知情報を使用して、診断および検証用のログシステムを作成することもできます。

イベントリスナーを実装して、イベントをキャプチャし、それに応答します。 多くのイベントには `MediaPlayerNotification` ステータスの通知。

`MediaPlayerNotification` は、プレーヤーのステータスに関連する情報を提供します。

TVSDK は、 `MediaPlayerNotification` 通知。 各通知には、次の情報が含まれます。

* タイムスタンプ
* 次の要素で構成される診断メタデータ：

   * `type`：情報、警告またはエラー。
   * `code`：通知の数値表現。
   * `name`：人間が判読できる、通知の説明（SEEK_ERROR など）
   * `metadata`：通知に関する関連情報を含むキーと値のペア。 例えば、 `URL` は通知に関連する URL を示す値を提供します。

   * `innerNotification`：別のへの参照 `MediaPlayerNotification` オブジェクトを直接表示します。

この情報をローカルに保存して後で分析したり、ログ記録やグラフィカル表示のためにリモートサーバーに送信したりできます。

## 通知システムの設定 {#set-up-your-notification-system}

通知をリッスンしたり、独自の通知を通知履歴に追加したりできます。

Primetime Player 通知システムの中心は、 `Notification` クラス。スタンドアロンの通知を表します。

The `NotificationHistory` クラスは、通知を蓄積するメカニズムを提供します。 Notifications のコレクションを表す通知 (NotificationHistoryItem) オブジェクトのログを格納します。

通知を受け取るには：

* 通知をリッスンする
* 通知履歴に通知を追加する

1. 状態の変更をリッスンします。
1. の実装 `MediaPlayer.PlaybackEventListener.onStateChanged` コールバック。
1. TVSDK は、2 つのパラメーターをコールバックに渡します。

   * 新しい状態 ( `MediaPlayer.PlayerState`)
   * A `MediaPlayerNotification` object

## リアルタイムログとデバッグの追加 {#add-real-time-logging-and-debugging}

通知を使用して、ビデオアプリケーションにリアルタイムのログを実装できます。

通知システムを使用すると、システムに過度の負荷をかけることなく、診断および検証のログおよびデバッグ情報を収集できます。

>[!IMPORTANT]
>
>ログバックエンドは実稼動環境の設定に含まれていないので、高負荷トラフィックを処理するとは想定されていません。 実装を完全に完了する必要がない場合は、システムの過負荷を防ぐために、データ送信の効率を考慮します。

次に、通知の取得方法の例を示します。

1. TVSDK 通知システムで収集されるデータに対して定期的にクエリを実行する、ビデオアプリケーション用のタイマーベースの実行スレッドを作成します。

1. タイマーの間隔が長すぎて、イベントリストのサイズが小さすぎる場合、通知イベントリストはオーバーフローします。 このオーバーフローを回避するには、次のいずれかの操作を行います。

   * 新しいイベントをポーリングするスレッドを駆動する時間間隔を短くします。
   * 通知リストのサイズを増やします。

1. 最新の通知イベントエントリを JSON 形式でシリアル化し、後処理用にリモートサーバーに送信します。

   次に、リモートサーバーは、提供されたデータをリアルタイムでグラフィカルに表示できます。
1. 通知イベントの損失を検出するには、イベントインデックスの値の順序にギャップを探します。

   各通知イベントにはインデックス値があり、 `session.NotificationHistory` クラス。

## ID3 タグ {#id-tags}

ID3 タグは、ファイルのタイトルやアーティスト名など、オーディオまたはビデオファイルに関する情報を提供します。 TVSDK は、HLS ストリームのトランスポートストリーム (TS) セグメントレベルで ID3 タグを検出し、イベントをディスパッチします。 タグからデータを抽出できます。

>[!IMPORTANT]
>
>TVSDK は、可能なエンコーディング (ASCII、UTF8、UTF16-BE、UTF16-LE) のいずれかで、オーディオ (AAC) およびビデオ (H.264) ストリームの ID3 メタデータ（バージョン 2.3.0 または 2.4.0）を認識します。 認識されるバージョンまたは形式のいずれにも含まれない ID3 タグは無視されます。 未指定のエンコードは UTF8 として扱われます。

TVSDK は、ID3 メタデータを検出すると、次のデータを含む通知を発行します。

* InfoCode = 303007
* TYPE = ID3
* NAME =存在しません
* ID = 0

1. のイベントリスナーを実装します。 `MediaPlayer.PlaybackEventListener#onTimedMetadata(TimeMetadata timeMetadata)` そして次に登録します。 `MediaPlayer` オブジェクト。

   TVSDK は、ID3 メタデータを検出すると、このリスナーを呼び出します。

   >[!NOTE]
   >
   >カスタム広告キューは同じを使用します `onTimedMetadata` イベントを使用して、新しいタグの検出を示します。 カスタム広告キューはマニフェストレベルで検出され、ID3 タグがストリームに埋め込まれるので、これによって混乱が生じることはありません。 詳しくは、 custom-tags-configure を参照してください。

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
