---
description: Browser TVSDKライブラリの通知部分を使用すると、診断や検証に役立つログおよびデバッグシステムを作成できます。
seo-description: Browser TVSDKライブラリの通知部分を使用すると、診断や検証に役立つログおよびデバッグシステムを作成できます。
seo-title: 通知システム
title: 通知システム
uuid: 69c4ff1d-3167-413b-ab49-942a5ddc34d7
translation-type: tm+mt
source-git-commit: 040655d8ba5f91c98ed0584c08db226ffe1e0f4e

---


# 通知システム {#notification-system}

Browser TVSDKライブラリの通知部分を使用すると、診断や検証に役立つログおよびデバッグシステムを作成できます。

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

ブラウザーTVSDKのAPIにはス *ローポリシ* ーがありません。 ほとんどのメソッドは、メ `PSDKErrorCode` ソッドが正常に実行されたかどうかを示す値を返します。 可能なすべての値の完全なリストについては、ブ `PSDKErrorCode` ラウザーTVSDK APIリファレンスを参照してください。

非同期エラーは、特定のイベントを通じて通知されます。

ブラウザーTVSDKは、イベントをデ `MediaPlayer` ィスパッチして、プレーヤーのアクティビティに関する情報を提供します。 これらのイベントを取得して応答するには、イベントリスナーを実装する必要があります。

>[!TIP]
>
>主要なイベントと情報は、Webブラウザーのコンソールに記録されます。

## 通知のリッスン {#section_06B96633433D497E842FB7ADD5F2C7DA}

通知をリッスンし、独自の通知を通知履歴に追加できます。 ブラウザーTVSDK通知システムの中核は、スタ `Notification` ンドアロン通知を表すクラスです。

通知をリッスンするようにアプリケーションを設定するには：

1. MediaPlayerのステータス変更をリッスンするには、MediaPlayerインスタンスを使用します。

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. コールバックを実装します。

   このコールバックは、のインスタンスを受 `AdobePSDK.MediaPlayerStatusChangeEvent`け取り、ブラウザーTVSDKは、このイベントオブジェクトを、新しいプレーヤー状態を含むコールバックに渡します。
1. アプリケーションは、このインスタンスを使用して、ブラウザーTVSDKがディスパッチする他のイベントをリッスン `MediaPlayer` できます。

