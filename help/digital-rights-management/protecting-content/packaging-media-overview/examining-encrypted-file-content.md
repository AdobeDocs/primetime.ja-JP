---
seo-title: 暗号化されたファイルの内容を調べています
title: 暗号化されたファイルの内容を調べています
uuid: 1b3318f6-0850-43f2-9127-c72ea81a1bdf
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 暗号化されたファイルの内容を調べています{#examining-encrypted-file-content}

Java APIを使用して、暗号化されたメディアファイルの内容を確認できます。

暗号化されたファイルの内容を調べるには：

1. 開発環境を設定し、すべてのJARファイルを含めます。 詳しくは、 *プロジェクトのSDKの設定* （英語のみ）を参照してください。
1. インスタンスを作 `MediaEncrypter` 成します。
1. 暗号化されたファイルをメソッドに渡 `MediaEncrypter.examineEncryptedContent` し、メソッドはオブジェクトを返 `KeyMetaData` します。

1. オブジェクト内の情報を調 `KeyMetaData` べます。

暗号化されたファイルからDRMメタデータを抽出する方法を説明するサンプルコードについては、参照実装コ `com.adobe.flashaccess.samples.mediapackager.ExamineContent` マンドラインツールディレクトリのを参照して [!DNL samples/] ください。
