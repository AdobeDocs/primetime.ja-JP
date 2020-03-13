---
seo-title: 暗号化されたファイルの内容を調べています
title: 暗号化されたファイルの内容を調べています
uuid: 2132fac7-5f11-4308-b511-ed4f216527a6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 暗号化されたファイルの内容を調べています {#examining-encrypted-file-content}

Java APIを使用してFLVまたはF4Vファイルのコンテンツを調べるには、次の手順を実行します。

1. 開発環境を設定し、「プロジェクト内の開発環境の設定」に記載されてい [るすべてのJARファイルを](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) 含めます。
1. インスタンスを作 `MediaEncrypter` 成します。
1. 暗号化されたファイルをメソッドに渡 `MediaEncrypter.examineEncryptedContent` し、メソッドはオブジェクトを返 `KeyMetaData` します。
1. オブジェクト内の情報を調 `KeyMetaData` べます。

暗号化されたファイルからDRMメタデータを抽出する方法を示すサンプルコードについては、リファレンス実装のコ `com.adobe.flashaccess.samples.mediapackager.ExamineContent` マンドラインツールの「samples」ディレクトリのを参照してください。
