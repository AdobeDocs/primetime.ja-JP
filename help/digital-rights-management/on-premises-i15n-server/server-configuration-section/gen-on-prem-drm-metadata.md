---
title: オンプレミスDRMメタデータの生成
description: オンプレミスDRMメタデータの生成
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 1%

---


# オンプレミスDRMメタデータの生成{#generate-the-on-premises-drm-metadata}

[!DNL CreateMetadata.jar]ユーティリティは[!DNL create_metadata]フォルダーに含まれています。 このユーティリティのポイントは、オンプレミスDRMメタデータを作成し、指定したオンプレミス個別化サーバーに対してクライアントが個別化プロセスを実行するように開始することです。

1. 次のファイルを使用して、Primetime DRM参照実装の更新 — コマンドラインツール

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

      2つのJARファイルは[!DNL Command Line Tools/libs]フォルダーに格納できます。 [!DNL createMetadata.properties]ファイルは、[!DNL flashaccesstools.properties]ファイルの隣に置くことができます。

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

メタデータのサンプル作成を示す[!DNL examplecreate.sh]スクリプトが含まれています。 メタデータを生成する前に、スクリプトファイルとプロパティファイルの両方で、License Server URLと個別化サーバーURLを設定してください。

ユーティリティの入力は次のとおりです。

* `createMetadata.properties`  — デフォルトのポリシー、証明書の場所、パスワードなどを含むプロパティファイル。
* `indivCert`  — 個別化トランスポート証明書を含むPKCS12ファイル
* `indivURL`  — オンプレミス個別化サーバーのURL

出力ファイルは、DRMクライアントで使用されるオンプレミスのDRMメタデータファイルです。 例：

```
java -jar libs/CreateMetadata.jar -c createMetadata.properties -indivCert i15n_transport.cer
-indivURL https://[YOURINDIVSERVER:PORT] onpremdrm.metadata
```

.