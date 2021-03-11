---
description: ブラウザーTVSDKライブラリの通知部分を使用すると、診断や検証に役立つログおよびデバッグシステムを作成できます。
title: 通知システム
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# 通知システム{#notification-system}

ブラウザーTVSDKライブラリの通知部分を使用すると、診断や検証に役立つログおよびデバッグシステムを作成できます。

<!--<a id="section_EC5DBE8DDA434B70A01FA2F3EF4618BD"></a>-->

ブラウザーTVSDKのAPIには、*スロー*&#x200B;ポリシーがありません。 ほとんどのメソッドは、メソッドが正常に実行されたかどうかを示す`PSDKErrorCode`値を返します。 可能なすべての`PSDKErrorCode`値の完全なリストについては、ブラウザーTVSDK APIリファレンスを参照してください。

非同期エラーは、特定のイベントを通じて通知されます。

ブラウザーTVSDKは、`MediaPlayer`イベントをディスパッチして、プレイヤーのアクティビティに関する情報を提供します。 これらのイベントを取得して応答するには、イベントリスナーを実装する必要があります。

>[!TIP]
>
>主要なイベントと情報は、Webブラウザーコンソールに記録されます。

## 通知をリッスン{#section_06B96633433D497E842FB7ADD5F2C7DA}

通知をリッスンし、独自の通知を通知履歴に追加できます。 ブラウザーTVSDK通知システムの中核は`Notification`クラスで、スタンドアロン通知を表します。

通知をリッスンするアプリケーションを設定するには：

1. MediaPlayerインスタンスを使用して、MediaPlayerのステータス変更をリッスンします。

   ```js
   player.addEventListener( 
         AdobePSDK.PSDKEventType.STATUS_CHANGED, onStatusChange);
   ```

1. コールバックを実装します。

   このコールバックは`AdobePSDK.MediaPlayerStatusChangeEvent`のインスタンスを受け取り、Browser TVSDKは、このイベントオブジェクトを、新しいプレイヤー状態を含むコールバックに渡します。
1. アプリケーションは、`MediaPlayer`インスタンスを使用して、Browser TVSDKがディスパッチする他のイベントをリッスンできます。

