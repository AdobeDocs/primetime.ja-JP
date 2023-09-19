---
description: Browser TVSDK ライブラリの通知部分を使用すると、診断や検証の目的で役立つログとデバッグシステムを作成できます。
title: 通知システム
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# 通知システム {#notification-system}

Browser TVSDK ライブラリの通知部分を使用すると、診断や検証の目的で役立つログとデバッグシステムを作成できます。

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

ブラウザー TVSDK には、 *投げなし* ポリシーを設定する必要があります。 ほとんどのメソッドは、 `PSDKErrorCode` 値を使用して、メソッドが正常に実行されたかどうかを示します。 可能なすべての `PSDKErrorCode` の値については、 Browser TVSDK API リファレンスを参照してください。

非同期エラーは、特定のイベントを通じて通知されます。

ブラウザー TVSDK がディスパッチする `MediaPlayer` イベントを使用して、プレーヤーのアクティビティに関する情報を提供します。 これらのイベントを取得して応答するには、イベントリスナーを実装する必要があります。

>[!TIP]
>
>主要なイベントと情報は、Web ブラウザーコンソールに記録されます。

## 通知をリッスンする {#section_06B96633433D497E842FB7ADD5F2C7DA}

通知をリッスンし、独自の通知を通知履歴に追加できます。 ブラウザー TVSDK 通知システムの中心は、 `Notification` クラス。スタンドアロン通知を表します。

通知をリッスンするアプリケーションを設定するには、次の手順を実行します。

1. MediaPlayer インスタンスを使用して、 MediaPlayer ステータスの変更をリッスンします。

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. コールバックを実装します。

   このコールバックは、 `AdobePSDK.MediaPlayerStatusChangeEvent`を呼び出し、ブラウザー TVSDK は、このイベントオブジェクトを、新しいプレーヤー状態を格納するコールバックに渡します。
1. アプリケーションは、を使用して、Browser TVSDK によってディスパッチされる他のイベントをリッスンできます。 `MediaPlayer` インスタンス。
