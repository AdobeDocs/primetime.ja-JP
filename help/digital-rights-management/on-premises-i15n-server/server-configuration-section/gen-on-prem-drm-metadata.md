---
seo-title: オンプレミスDRMメタデータの生成
title: オンプレミスDRMメタデータの生成
uuid: 89d53924-1a8d-42d4-a716-ce4f4566b6bf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# オンプレミスDRMメタデータの生成{#generate-the-on-premises-drm-metadata}

ユーテ [!DNL CreateMetadata.jar] ィリティがフォルダに含ま [!DNL create_metadata] れます。 このユーティリティのポイントは、オンプレミスのDRMメタデータを作成し、指定したオンプレミスの個別化サーバーに対してクライアントが個別化プロセスを実行するようにクライアントを開始することです。

1. 次のファイルを使用して、Primetime DRMリファレンスの実装 — コマンドラインツールを更新します。

   * [!DNL CreateMetadata.jar]
   * [!DNL commons-cli-1.2.jar]
   * [!DNL createMetadata.properties]

      この2つのJARファイルは、フォルダーに格納で [!DNL Command Line Tools/libs] きます。 ファイル [!DNL createMetadata.properties] は、ファイルの横に配置で [!DNL flashaccesstools.properties] きます。

<!--<a id="example_2116349CA33642CD9293EAD94A532ED8"></a>-->

メタデータの作成 [!DNL examplecreate.sh] 例を示すスクリプトが含まれています。 メタデータを生成する前に、スクリプトファイルとプロパティファイルの両方で、License Server URLとIndividualization Server URLを必ず設定してください。

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