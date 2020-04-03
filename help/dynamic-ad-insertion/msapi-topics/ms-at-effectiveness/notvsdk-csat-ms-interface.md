---
description: 現在のビデオに関する広告追跡情報を送信するURLを取得するには、オプションのpttrackingmode、pttrackingversionおよびpttrackingpositionクエリパラメーターを使用します。 応答は、追跡バージョン、およびビデオストリームがライブかオンデマンドか(VOD)によって異なります。
seo-description: 現在のビデオに関する広告追跡情報を送信するURLを取得するには、オプションのpttrackingmode、pttrackingversionおよびpttrackingpositionクエリパラメーターを使用します。 応答は、追跡バージョン、およびビデオストリームがライブかオンデマンドか(VOD)によって異なります。
seo-title: プレーヤーがマニフェストサーバーとやり取りするAPI
title: プレーヤーがマニフェストサーバーとやり取りするAPI
uuid: ab7a19e7-6c28-4960-a56b-3b33c525e6b3
translation-type: tm+mt
source-git-commit: a33e1f290fcf78e6f131910f6037f4803f7be98d

---


# プレーヤーがマニフェストサーバーとやり取りするAPI {#api-for-players-to-interact-with-the-manifest-server}

現在のビデオに関す `pttrackingmode`る広告追跡情報を送信するURLを取得するには、 `pttrackingversion``pttrackingposition` オプションの、、およびクエリの各パラメーターを使用します。 応答は、追跡バージョン、およびビデオストリームがライブかオンデマンドか(VOD)によって異なります。

## クエリパラメータ {#query-parameters}

|**pttrackingmode**|
例：pttrackingmode=simpleSpecifying simpleは、追跡情報を必要とすることをマニフェストサーバーに指示します。
追跡情報を要求する前に、M3U8を取得する要求に対して指定します。指定しない場合、マニフェストサーバーは#EXT-X-MARKERタグで追跡情報を返します。
または、単純な値以外の有効な値を指定した場合は、サーバー側の追跡が呼び出されます。

|**pttrackingversion**|
例：pttrackingversion=v2このパラメーターは、追跡情報を返す際に使用する形式をマニフェストサーバーに指示します( [ファイル形式](../../msapi-topics/ms-list-file-formats/ms-api-file-formats.md))。
追跡情報を要求する前に、M3U8を取得する要求で指定します。指定しない場合、または無効な値を指定する場合、マニフェストサーバーはv1を使用します。

|**pttrackingposition**|
例：pttrackingpositionこのパラメーターは、マニフェストサーバーにビデオの追跡情報をM3U8ファイル内のJSONまたはVMAPオブジェクトとして返すように指示します。マニフェストサーバーは指定された値を無視し、そのセッションに関する追跡情報をすべて送信します。 値が渡されない場合、マニフェストサーバーは要求されたM3U8ファイルを返します。
