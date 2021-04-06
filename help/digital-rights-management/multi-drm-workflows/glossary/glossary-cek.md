---
title: 用語集
description: 特別な定義を必要とする、よく使用される用語です。
exl-id: 4e7874f7-c5c0-4f2c-ada2-a0da3ed4d4bf
translation-type: tm+mt
source-git-commit: 3e63c187f12d1bff53370bbcde4d6a77f58f3b4f
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# 用語集{#glossary}

特別な定義を必要とする、よく使用される用語です。

## コンテンツ暗号化キー{#content-encryption-key}

ユーティリティによって生成されたコンテンツ暗号化キー(CEK)は、その後、コンテンツパッケージャーが保護する必要のあるコンテンツを準備する際に使用されます。
このユーティリティは、16進数で長さ16バイトのキーを生成します。
このガイドは、CEKのパラメーター名と値の名前の次の変種を、注意とエラーメッセージ、ファイル、およびコマンドのサンプルに示しています。

* コンテンツキー
* `&contentKey=`
* `?cek=`
* `<CEK>`
* `[YOUR CONTENT KEY]`

CEKのファイル名は次のように表示されます。

* `keyfile.bin`
* `creds/fairplaybin`
* `Jaigo_DASH/_info/key.B64.random`

CEK自体は、暗号化するだけでなく、鍵管理システムに保存することもできます。 このガイドは、ストレージのインデックスをCEKストレージID CEKSIDと呼びます。 キー暗号化キー(KEK)という用語は第2レベルの暗号化キーを指し、`ek`という用語はその暗号化の値を指します。
一部の呼び出しでは、CEKとCEKストレージID CEKSIDの両方を使用し、ストレージから取得したCEKは、呼び出しで提供されたCEKと一致する必要があります。
FairPlayを使用したHLS Offlineの場合は、`persistentContentKey`も有効期限切れに設定できます。

## コンテンツ暗号化キーのストレージID {#content-encryption-key-storage-id}

コンテンツ暗号化キーストレージID(CEKSID)は、キー管理システムからコンテンツ暗号化キーを取得するためのIDです。

CEKSIDは、
* キーID
* コンテンツID
* `&kid`

## ユーザー認証子{#customer-authenticator}

ExpressplayのAPIへのリクエストでの認証用のキー。 要求には、トークンの要求を含めることができます。
