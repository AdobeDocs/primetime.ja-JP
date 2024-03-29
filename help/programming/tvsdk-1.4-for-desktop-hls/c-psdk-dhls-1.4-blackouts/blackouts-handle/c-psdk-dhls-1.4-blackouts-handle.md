---
description: ライブビデオストリームでブラックアウトを処理し、ブラックアウト中に代替コンテンツを提供できます。
title: ライブストリーム内のブラックアウトの処理
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# ライブストリーム内のブラックアウトの処理{#handle-blackouts-in-live-streams}

ライブビデオストリームでブラックアウトを処理し、ブラックアウト中に代替コンテンツを提供できます。

ライブストリームでブラックアウトが発生した場合、プレーヤーではイベントハンドラーを使用してブラックアウトを検出し、メインストリームを視聴する資格のないユーザーに代替コンテンツを提供します。 プレーヤーでは、ブラックアウト期間の開始と終了を検出し、再生をメインストリームから代替ストリームに切り替え、ブラックアウト期間が終了したらメインストリームに切り替えます。

クライアントアプリで、TVSDK のブラックアウトタグをサブスクライブします。 新規の通知を受けたとき *時間指定メタデータ* オブジェクトが存在する場合、時間指定メタデータオブジェクトのデータを解析して、オブジェクトがブラックアウトのエントリを示しているか、終了を示しているかを識別します。 識別されたブラックアウトに対して、関連する TVSDK 要素を呼び出して、ブラックアウトの開始時に代替コンテンツに切り替え、ブラックアウトが終了したときに再びメインコンテンツに戻ります。

>[!TIP]
>
>キーは、コンテンツが再生される前に、引き続きマニフェストからダウンロードされます。

ブラックアウト期間が終了した後にユーザーがライブストリームに接続し、ブラックアウト期間まで時間を遡ると、コンテンツが再生されます。

>[!IMPORTANT]
>
>すべてのキーリクエストが失敗した場合、マニフェストを解析する際にエラーがスローされます。 一部のリクエストが失敗し、一部が成功した場合、 TVSDK はコンテンツの再生を試みます。 TVSDK がコンテンツのセクションを再生しようとしたが、このコンテンツを復号化する有効なキーがない場合は、エラーが返されます。

ライブストリーム内のブラックアウトを処理するには：

1. ライブストリームマニフェスト内のブラックアウトタグをサブスクライブすることで、ブラックアウトタグを検出するアプリを設定します。

   TVSDK は、ブラックアウトタグを単独では検出しません。マニフェストファイルの解析中にタグを検出した場合に通知を受け取るには、ブラックアウトタグをサブスクライブする必要があります。
1. プレーヤーがサブスクライブしているタグに対するイベントリスナーを作成します。

   プレーヤーがフォアグラウンド（メインコンテンツ）またはバックグラウンド（代替コンテンツ）のストリームマニフェストで（ブラックアウトタグなど）をサブスクライブした場合、 TVSDK は `TimedMetadataEvent` とは、 `TimedMetadataObject` （の） `TimedMetadataEvent`.
1. フォアグラウンドストリームとバックグラウンドストリームの両方に対して、時間指定メタデータイベントのハンドラーを実装します。

   これらのハンドラーで、時間指定メタデータイベントオブジェクトから、ブラックアウト期間の開始時間と終了時間を取得します。
1. を準備する `MediaPlayer` ブラックアウトの場合

   次の場合に `MediaPlayer` が PREPARED 状態になると、ブラックアウト範囲を計算して準備し、 `MediaPlayer` オブジェクト

1. 再生ヘッドの位置を更新するたびに、 `TimedMetadataObjects`.

   ここで、プレーヤーがブラックアウトの開始と終了を検出し、ブラックアウトの発生時間を追跡します。

1. ブラックアウト期間の開始および終了時にコンテンツを切り替えるメソッドを作成します。

   ブラックアウト期間が開始したら、メインコンテンツをバックグラウンドに切り替え、代替コンテンツをメインストリームに切り替えます。 バックグラウンドで元のマニフェストを取得して解析し続け、「ブラックアウト終了」タグを確認し続けます。これにより、ブラックアウトが終了したときにプレーヤーが元のストリームに再結合できるようになります。
