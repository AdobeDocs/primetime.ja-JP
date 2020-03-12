---
uuid: 2d927ae8-4c4b-4b64-88b8-9c86430e226c
translation-type: tm+mt
source-git-commit: c78d3c87848943a0be3433b2b6a543822a7e1c15

---


# 用語集 {#glossary}

特別な定義が必要な、よく使用される用語。

## コンテンツ暗号化キー {#content-encryption-key}

ユーティリティによって生成されたコンテンツ暗号化キー(CEK)は、その後、保護する必要のあるコンテンツを準備する際に、コンテンツパッケージャーによって使用されます。
このユーティリティは、16進数で16バイトの長さのキーを生成します。
このガイドは、CEKのパラメータ名と値名の次のバリエーションを、メモおよびエラーメッセージ、ファイル、およびコマンドのサンプルで示しています。

* コンテンツキー
* `&contentKey=`
* `?cek=`
* `<CEK>`
* `[YOUR CONTENT KEY]`

CEKのファイル名は次のように表示されます。

* `keyfile.bin`
* `creds/fairplaybin`
* `Jaigo_DASH/_info/key.B64.random`

CEK自体は、暗号化されるだけでなく、鍵管理システムにも格納できます。 このガイドでは、ストレージインデックスをCEK Storage ID CEKSIDと呼びます。 キー暗号化キー(KEK)という用語は第2レベルの暗号化キーを指し、その暗 `ek` 号化の値を指します。
呼び出しによっては、CEKとCEK Storage ID CEKSIDの両方を使用し、ストレージから取得したCEKは、呼び出しで指定したCEKと一致する必要があります。
FairPlayを使用したHLSオフラインの場合、期限切れに設 `persistentContentKey` 定できるものもあります。

## コンテンツ暗号化キーストレージID {#content-encryption-key-storage-id}

コンテンツ暗号化キーストレージID(CEKSID)は、キー管理システムからコンテンツ暗号化キーを取得するためのIDです。

CEKSIDは、
* キーID
* コンテンツID
* `&kid`

## ユーザー認証子 {#customer-authenticator}

ExpressplayのAPIへの要求での認証用のキー。 要求にはトークンの要求を含めることができます。