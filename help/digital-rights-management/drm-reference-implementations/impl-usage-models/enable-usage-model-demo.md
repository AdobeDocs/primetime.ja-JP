---
seo-title: 使用モデルのデモを有効にする
title: 使用モデルのデモを有効にする
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 6e949c2f88deef88f0d0ac95b18c006da1c89d2f

---


# 使用モデルのデモを有効にする{#enable-the-usage-model-demo}

1. パッケージ化時にカスタムプ `RI_UsageModelDemo=true` ロパティを指定します。

   Media Packagerコマンドラインツールを使用してコンテンツをパッケージ化する場合は、次のように入力します。

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>パッケージ化時にオプションのデモモードをアクティブ化しない場合、ライセンスサーバーは、処理する最初の有効なDRMポリシーに基づいてライセンスを発行します。

