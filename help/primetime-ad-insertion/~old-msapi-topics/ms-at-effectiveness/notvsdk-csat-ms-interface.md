---
description: 現在のビデオに関する広告追跡情報を送信するURLを取得するには、オプションのpttrackingmode、pttrackingversionおよびpttrackingpositionクエリパラメーターを使用します。 応答は、トラッキングバージョンや、ビデオストリームがライブかオンデマンド(VOD)かによって異なります。
seo-description: 現在のビデオに関する広告追跡情報を送信するURLを取得するには、オプションのpttrackingmode、pttrackingversionおよびpttrackingpositionクエリパラメーターを使用します。 応答は、トラッキングバージョンや、ビデオストリームがライブかオンデマンド(VOD)かによって異なります。
seo-title: プレーヤーがマニフェストサーバーとやり取りするためのAPI
title: プレーヤーがマニフェストサーバーとやり取りするためのAPI
uuid: ab7a19e7-6c28-4960-a56b-3b33c525e6b3
translation-type: tm+mt
source-git-commit: e1e33d3ac0aad44859cd49566331524da72ac7e4
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---


# プレーヤーがマニフェストサーバーとやり取りするためのAPI {#api-for-players-to-interact-with-the-manifest-server}

オプションの`pttrackingmode`、`pttrackingversion`および`pttrackingposition`クエリパラメーターを使用して、現在のビデオに関する広告トラッキング情報を送信するURLを取得します。 応答は、トラッキングバージョンや、ビデオストリームがライブかオンデマンド(VOD)かによって異なります。

## クエリパラメータ{#query-parameters}

**pttrackingmode**

例：`pttrackingmode=simple`
simpleを指定すると、マニフェストサーバーに追跡情報を必要とすることを指示します。
トラッキング情報を要求する前に、M3U8を取得する要求に対して指定します。指定しない場合、マニフェストサーバーは、#EXT-X-MARKERタグでトラッキング情報を返します。
単純な値以外の有効な値を指定すると、サーバー側の追跡が呼び出されます。

**pttrackingversion**

例：`pttrackingversion=v2`
このパラメーターは、追跡情報を返すために使用する形式をマニフェストサーバーに指示します（[ファイル形式](/help/primetime-ad-insertion/~old-msapi-topics/ms-list-file-formats/ms-api-file-formats.md)を参照）。
トラッキング情報を要求する前に、M3U8を取得する要求に対して指定します。指定しない場合、または無効な値を指定する場合、マニフェストサーバーはv1を使用します。

**pttrackingposition**

例：`pttrackingposition`
このパラメーターは、マニフェストサーバーに、ビデオのトラッキング情報をM3U8ファイル内のJSONまたはVMAPオブジェクトとして返すように指示します。マニフェストサーバーは、指定された値を無視し、そのセッションに対して持つすべてのトラッキング情報を送信します。 値が渡されない場合、マニフェストサーバーは要求されたM3U8ファイルを返します。
