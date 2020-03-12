---
seo-title: 使用モデルのデモを有効にする
title: 使用モデルのデモを有効にする
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 使用モデルのデモを有効にする{#enable-the-usage-model-demo}

1. パッケージ化時にカスタムプ `RI_UsageModelDemo=true` ロパティを指定します。

   Media Packagerコマンドラインツールを使用してコンテンツをパッケージ化する場合は、次のように入力します。

   ```
   java -jar AdobeMediaPackager.jar [
   
<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true

```
>[!NOTE] {class="- topic/note "}
>
>If you do not activate the optional demo mode at packaging time, the license server issues a license based on the first valid DRM policy it processes.

