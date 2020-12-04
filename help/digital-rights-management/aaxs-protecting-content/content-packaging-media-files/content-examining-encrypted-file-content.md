---
seo-title: 暗号化されたファイルの内容を調べる
title: 暗号化されたファイルの内容を調べる
uuid: 2132fac7-5f11-4308-b511-ed4f216527a6
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---


# 暗号化されたファイルの内容を調べています{#examining-encrypted-file-content}

Java APIを使用してFLVまたはF4Vファイルのコンテンツを調べるには、次の手順を実行します。

1. 開発環境を設定し、プロジェクト内の[開発環境の設定](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md)で説明されているすべてのJARファイルを含めます。
1. `MediaEncrypter`インスタンスを作成します。
1. 暗号化されたファイルを`MediaEncrypter.examineEncryptedContent`メソッドに渡し、`KeyMetaData`オブジェクトを返します。
1. `KeyMetaData`オブジェクト内の情報をInspectします。

暗号化されたファイルからDRMメタデータを抽出する方法を示すサンプルコードについては、リファレンス実装のコマンドラインツールの「samples」ディレクトリの`com.adobe.flashaccess.samples.mediapackager.ExamineContent`を参照してください。
