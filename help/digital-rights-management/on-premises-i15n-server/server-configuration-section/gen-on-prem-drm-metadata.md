---
title: オンプレミスの DRM メタデータを生成する
description: オンプレミスの DRM メタデータを生成する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# オンプレミスの DRM メタデータを生成する{#generate-the-on-premises-drm-metadata}

A [!DNL CreateMetadata.jar] ユーティリティは、 [!DNL create_metadata] フォルダー。 このユーティリティの目的は、指定した On Premises Individualization Server に対して個別化プロセスを実行するクライアントを開始する On Premises DRM メタデータを作成することです。

1. Primetime DRM 参照実装 — コマンドラインツールを次のファイルに更新します。

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

     2 つの JAR ファイルは、 [!DNL Command Line Tools/libs] フォルダー。 The [!DNL createMetadata.properties] ファイルは、 [!DNL flashaccesstools.properties] ファイル。

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

次に含まれる： [!DNL examplecreate.sh] メタデータのサンプル作成を示すスクリプト。 メタデータを生成する前に、スクリプトファイルとプロパティファイルの両方で License Server URL と Individualization Server URL を必ず設定してください。

ユーティリティの入力は次のとおりです。

* `createMetadata.properties`  — デフォルトのポリシー、証明書の場所、パスワードなどを含むプロパティファイル。
* `indivCert`  — 個別化トランスポート証明書を含む PKCS12 ファイル
* `indivURL`  — オンプレミスの個別化サーバーの URL

出力ファイルは、DRM クライアントが使用する On Premises DRM メタデータファイルです。 例：

```
java -jar libs/CreateMetadata.jar -c createMetadata.properties -indivCert i15n_transport.cer
-indivURL https://[YOURINDIVSERVER:PORT] onpremdrm.metadata
```

.
