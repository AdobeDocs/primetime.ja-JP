---
description: プレイリスト全体が見つからない場合（トップレベルのマニフェストファイルで指定されている M3U8 ファイルがダウンロードされない場合など）、 TVSDK は復元を試みます。 回復できない場合は、次の手順がアプリケーションによって決定されます。
title: プレイリストのフェイルオーバーが見つかりません
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# プレイリストのフェイルオーバーが見つかりません{#missing-playlist-failover}

プレイリスト全体が見つからない場合（トップレベルのマニフェストファイルで指定されている M3U8 ファイルがダウンロードされない場合など）、 TVSDK は復元を試みます。 回復できない場合は、次の手順がアプリケーションによって決定されます。

中解像度のビットレートに関連付けられているプレイリストがない場合、 TVSDK は同じ解像度のバリアントプレイリストを検索します。 同じ解像度が見つかった場合は、バリアントプレイリストとセグメントを一致する位置からダウンロードし始めます。 TVSDK が同じ解像度のプレイリストを見つけられない場合は、他のビットレート再生リストとそのバリアントを順に切り替えようとします。 すぐ下のビットレートが最初の選択肢で、その次にそのバリアントがその後に続きます。 有効なプレイリストを見つけようとして、低いビットレートの再生リストとそのバリアントがすべて使い果たされた場合、 TVSDK は最上位のビットレートに移動し、そこからカウントダウンします。 有効なプレイリストが見つからない場合、プロセスは失敗し、プレーヤーは ERROR 状態に移行します。

この状況の処理方法は、アプリケーションによって決定されます。 例えば、プレーヤーアクティビティを閉じて、ユーザーをカタログアクティビティに誘導するとします。 関心のあるイベントは、 `STATE_CHANGED` イベントを呼び出し、対応するコールバックが `onStateChanged` メソッド。 プレーヤーが内部状態を ERROR に変更したかどうかを監視するコードを次に示します。

```java
case ERROR: 
    getActivity().finish(); // this is where we close the current activity (the Player activity) 
    break;
```

詳しくは、 [!DNL PlayerFragment.java] ファイルを次のように指定します。

```
[…]/samples/PrimetimeReference/src/PrimetimeReference/src/com/adobe/primetime/reference/ui/player/
```

クライアント側のネットワークがダウンしている場合は、このコードを使用して検証できます。

```
psdkutils::PSDKString 
getNetworkDownVerificationUrl() const { return 
_networkDownVerificationUrl; }
```

API は、クライアント側のネットワークがダウンしているかどうかを確認するために使用される URL を提供します。 HTTP リクエストに対して HTTP 応答コード 200 を返す有効な URL を指定する必要があります。

```
psdkutils::PSDKErrorCode 
 setNetworkDownVerificationUrl(psdkutils::PSDKString value) {  
_networkDownVerificationUrl = value; return psdkutils::kECSuccess; }
```

setNetworkDownVerificationUrl が設定されていない場合、 TVSDK はデフォルトで MainManifest の URL を使用して、ネットワークがダウンしているかどうかを示します。
