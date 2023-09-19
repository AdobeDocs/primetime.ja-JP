---
title: 用語集
description: 特別な定義を必要とする、頻繁に使用される用語。
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# 用語集 {#glossary}

特別な定義を必要とする、頻繁に使用される用語。

## コンテンツ暗号化キー {#content-encryption-key}

ユーティリティによって生成されたコンテンツ暗号化キー (CEK) は、その後、保護が必要なコンテンツを作成する際にコンテンツパッケージャによって使用されます。
このユーティリティは、16 進数で長さ 16 バイトのキーを生成します。
このガイドでは、CEK のパラメータ名と値名の次のバリエーションを、注記とエラーメッセージ、ファイル、およびコマンドのサンプルに示します。

* コンテンツキー
* `&contentKey=`
* `?cek=`
* `<CEK>`
* `[YOUR CONTENT KEY]`

CEK のファイル名は次のように表示されます。

* `keyfile.bin`
* `creds/fairplaybin`
* `Jaigo_DASH/_info/key.B64.random`

CEK 自体は、暗号化するだけでなく、鍵管理システムに保存することもできます。 このガイドでは、ストレージインデックスを CEK ストレージ ID CEKSID と呼びます。 キー暗号化キー (KEK) という用語は、第 2 レベルの暗号化キーと、 `ek` は、その暗号化の値を参照します。
一部の呼び出しでは、CEK と CEK Storage ID CEKSID の両方を使用し、ストレージから取得した CEK は呼び出しで提供された CEK と一致する必要があります。
FairPlay を使用した HLS Offline の場合、 `persistentContentKey` 有効期限切れに設定できます。

## コンテンツ暗号化キーストレージ ID {#content-encryption-key-storage-id}

Content Encryption Key Storage ID(CEKSID) は、鍵管理システムからコンテンツ暗号化鍵を取得するための ID です。

CEKSID は、
* キー ID
* コンテンツ ID
* `&kid`

## ユーザー認証子 {#customer-authenticator}

Expressplay の API へのリクエストでの認証のためのキー。 リクエストには、トークンに対するリクエストを含めることができます。
