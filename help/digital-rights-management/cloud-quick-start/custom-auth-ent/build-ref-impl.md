---
seo-title: BEESリファレンスの実装の作成
title: BEESリファレンスの実装の作成
uuid: c9358188-e626-4f99-a02c-4928b06d6ae2
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# BEESリファレンスの実装の作成 {#build-the-bees-reference-implementation}

Java 1.6.0_24以降を使用していることを確認します。
1. およびなど、必要な空のパスを `tomcatdir` 入力 `fasterxmldir` し、 [!DNL build-bees.xml]

   FasterXML/Jacksonが含まれています。 また、https://jar-download.com/artifacts/com.fasterxml.jackson.coreからダウンロードすることもで [きます](https://jar-download.com/artifacts/com.fasterxml.jackson.core)。
1. 別のバージョンのJacksonライブラリを [!DNL build.common.xml] 使用する場合は、で実際のjarファイル名を更新します。
1. 次のターゲット `all` を実行しま [!DNL build-bees.xml]す。

   ```
   ant -f build-bees.xml
   ```

フォルダ [!DNL bees.war] ーにが作成され [!DNL bees-build/wars] ます。