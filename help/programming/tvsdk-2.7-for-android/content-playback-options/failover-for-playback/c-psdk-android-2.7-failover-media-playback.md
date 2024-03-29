---
description: ライブおよびビデオオンデマンド (VOD) メディアの場合、 TVSDK は、中解像度ビットレートに関連付けられているプレイリストのダウンロードで再生を開始し、そのプレイリストで定義されているメディアセグメントをダウンロードします。 高解像度ビットレートのプレイリストとそれに関連するメディアをすばやく選択し、ダウンロード処理を続行します。
title: メディアの再生とフェイルオーバー
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---

# メディアの再生とフェイルオーバー {#media-playback-and-failover}

ライブおよびビデオオンデマンド (VOD) メディアの場合、 TVSDK は、中解像度ビットレートに関連付けられているプレイリストのダウンロードで再生を開始し、そのプレイリストで定義されているメディアセグメントをダウンロードします。 高解像度ビットレートのプレイリストとそれに関連するメディアをすばやく選択し、ダウンロード処理を続行します。

## プレイリストのフェイルオーバーが見つかりません {#section_4EA0AEFA7FB84FCEA699DFB10B135368}

プレイリスト全体が見つからない場合（トップレベルのマニフェストファイルで指定されている M3U8 ファイルがダウンロードされない場合など）、 TVSDK は復元を試みます。 復元できない場合は、次の手順がアプリケーションによって決定されます。

中解像度のビットレートに関連付けられているプレイリストがない場合、 TVSDK は同じ解像度のバリアントプレイリストを検索します。 同じ解像度が見つかった場合、 TVSDK は、バリアントプレイリストとセグメントのダウンロードを、一致する位置から開始します。 プレーヤーが同じ解像度のプレイリストを見つけられない場合は、他のビットレート再生リストとそのバリアントを順に切り替えようとします。 すぐ下のビットレートが最初の選択肢で、その次にそのバリアントがその後に続きます。 有効なプレイリストを見つけようとして、低いビットレートの再生リストとそのバリアントがすべて使い果たされた場合、 TVSDK は最上位のビットレートに移動し、そこからカウントダウンします。 有効なプレイリストが見つからない場合、プロセスは失敗し、プレーヤーは ERROR 状態に移行します。

この状況の処理方法は、アプリケーションによって決定されます。 例えば、プレーヤーアクティビティを閉じて、ユーザーをカタログアクティビティに誘導するとします。 関心のあるイベントは、 `STATUS_CHANGED` イベントを呼び出し、対応するコールバックが `onStatusChanged` メソッド。 プレーヤーが内部ステータスをに変更したかどうかを監視するコードを以下に示します。 `ERROR`:

```java
... 
case ERROR: 
getActivity().finish(); // this is where we close the current activity (the Player activity) 
break; 
...
```

## セグメントフェイルオーバーが見つかりません {#section_D8DF377CCB644D7FB936796DA0CC5A4B}

セグメントが見つからない場合（特定のセグメントのダウンロードに失敗した場合など）、 TVSDK は様々なフェイルオーバー試行を通じて復元を試みます。 回復できない場合は、エラーを発行します。

例えば、マニフェストファイルが存在しない場合や、セグメントをダウンロードできない場合などに、サーバー上でセグメントが見つからない場合は、 TVSDK は次のオプションを試みてフェイルオーバーを試みます。

1. バリアントファイル内の同じビットレートで、同じセグメントに対するフェイルオーバーを試みます。
1. 同じファイル内の別のビットレートに切り替えます（ABR スイッチ）。
1. 使用可能なすべてのバリアントで使用可能なすべてのビットレートを順に切り替えます。
1. セグメントをスキップし、警告を表示します。

TVSDK は、別のセグメントを取得できない場合、トリガーを `CONTENT_ERROR` エラー通知。 この通知には、 `DOWNLOAD_ERROR` コード。 問題のあるストリームが代替オーディオトラックの場合、 TVSDK は `AUDIO_TRACK_ERROR` エラー通知。

ビデオエンジンが引き続きセグメントを取得できない場合、セグメントの連続スキップ数は 5 に制限されます。5 を超えた後は、再生が停止し、 TVSDK が `NATIVE_ERROR` を 5 番目のコードに置き換えます。

>[!NOTE]
>
>以下に、注意が必要な制限を示します。
>
>* フェイルオーバーが発生した場合、可変ビットレート (ABR) 制御パラメーターは考慮されません。
>
>  これは、フェイルオーバーメカニズムが、ビットレートプロファイルに関係なく、現在使用可能なプレイリストのいずれかをバックアップストリームとして使用するように設計されているためです。
>* フェイルオーバー操作中は、プロファイルスイッチが存在する場合があります。
>
>  プレイリストセグメントの 1 つのダウンロード中にエラーが発生した場合、許可される最小/最大ビットレートなどの ABR 制御パラメーターは無視されます。
>
