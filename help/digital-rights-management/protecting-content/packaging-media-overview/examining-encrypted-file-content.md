---
title: 暗号化されたファイルコンテンツの検査
description: 暗号化されたファイルコンテンツの検査
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '95'
ht-degree: 0%

---

# 暗号化されたファイルコンテンツの検査{#examining-encrypted-file-content}

Java API を使用して、暗号化されたメディアファイルの内容を確認できます。

暗号化されたファイルの内容を確認するには：

1. 開発環境を設定し、すべての JAR ファイルを含めます。 詳しくは、 *SDK の設定* を設定します。
1. の作成 `MediaEncrypter` インスタンス。
1. 暗号化されたファイルをに渡します。 `MediaEncrypter.examineEncryptedContent` メソッド。 `KeyMetaData` オブジェクト。

1. Inspect `KeyMetaData` オブジェクト。

暗号化されたファイルから DRM メタデータを抽出する方法を説明するサンプルコードについては、 `com.adobe.flashaccess.samples.mediapackager.ExamineContent` （「参照実装」コマンドラインツール） [!DNL samples/] ディレクトリ。
