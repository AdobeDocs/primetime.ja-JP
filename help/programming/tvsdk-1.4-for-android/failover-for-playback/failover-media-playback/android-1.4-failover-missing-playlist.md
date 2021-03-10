---
description: プレイリスト全体が見つからない場合（例えば、最上位のマニフェストファイルで指定されているM3U8ファイルがダウンロードされない場合）、TVSDKは回復を試みます。 回復できない場合は、次のステップをアプリケーションが決定します。
title: プレイリストのフェイルオーバーがありません
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---


# プレイリストのフェイルオーバー{#missing-playlist-failover}が見つかりません

プレイリスト全体が見つからない場合（例えば、最上位のマニフェストファイルで指定されているM3U8ファイルがダウンロードされない場合）、TVSDKは回復を試みます。 回復できない場合は、次のステップをアプリケーションが決定します。

中解像度ビットレートに関連付けられているプレイリストがない場合、TVSDKは同じ解像度のバリアントプレイリストを検索します。 同じ解像度が見つかった場合、開始はバリアントプレイリストとセグメントを一致する位置からダウンロードします。 TVSDKが同じ解像度プレイリストを見つけない場合、他のビットレートプレイリストとそのバリアントを順に切り替えようとします。 ビットレートがすぐ下の場合は最初の選択肢で、その次にそのバリアントなどがこれに該当します。 有効なプレイリストを見つけようとして、下位のビットレート再生リストとそのバリアントがすべて使い果たされた場合、TVSDKは最上位のビットレートに移動し、そこからカウントダウンします。 有効なプレイリストが見つからない場合、プロセスは失敗し、プレイヤーはERROR状態に移行します。

この状況の処理方法は、アプリケーションが決定できます。 例えば、プレイヤーアクティビティを閉じて、カタログアクティビティに移動させることができます。 関心のあるイベントは`STATE_CHANGED`イベントで、対応するコールバックは`onStateChanged`メソッドです。 以下のコードは、プレイヤーが内部状態をERRORに変更したかどうかを監視するものです。

```java
case ERROR: 
    getActivity().finish(); // this is where we close the current activity (the Player activity) 
    break;
```

詳しくは、SDKの[!DNL PlayerFragment.java]ファイルを参照してください。

```
[…]/samples/PrimetimeReference/src/PrimetimeReference/src/com/adobe/primetime/reference/ui/player/
```

クライアント側のネットワークがダウンしている場合は、このコードを使用して検証できます。

```
psdkutils::PSDKString 
getNetworkDownVerificationUrl() const { return 
_networkDownVerificationUrl; }
```

APIは、クライアント側のネットワークがダウンしているかどうかを検証するために使用されるURLを提供します。 HTTP要求時にhttp応答コード200を返す有効なURLを指定する必要があります。

```
psdkutils::PSDKErrorCode 
 setNetworkDownVerificationUrl(psdkutils::PSDKString value) {  
_networkDownVerificationUrl = value; return psdkutils::kECSuccess; }
```

setNetworkDownVerificationUrlが設定されていない場合、TVSDKは、デフォルトでMainManifest urlを使用して、ネットワークがダウンしているかどうかを示します。
