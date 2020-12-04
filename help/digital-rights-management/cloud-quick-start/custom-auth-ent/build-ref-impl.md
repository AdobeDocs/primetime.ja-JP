---
seo-title: BEESリファレンス実装の作成
title: BEESリファレンス実装の作成
uuid: c9358188-e626-4f99-a02c-4928b06d6ae2
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '78'
ht-degree: 0%

---


# BEESリファレンス実装の作成{#build-the-bees-reference-implementation}

Java 1.6.0_24以降を使用していることを確認します。
1. [!DNL build-bees.xml]の`tomcatdir`や`fasterxmldir`など、必要な空のパスを入力します

   FasterXML/Jacksonが含まれています。 また、[https://jar-download.com/artifacts/com.fasterxml.jackson.core](https://jar-download.com/artifacts/com.fasterxml.jackson.core)からダウンロードすることもできます。
1. Jacksonライブラリの別のバージョンを使用する場合は、[!DNL build.common.xml]の実際のjarファイル名を更新します。
1. `all`ターゲットの[!DNL build-bees.xml]を実行します。

   ```
   ant -f build-bees.xml
   ```

[!DNL bees.war]が[!DNL bees-build/wars]フォルダーに作成されます。