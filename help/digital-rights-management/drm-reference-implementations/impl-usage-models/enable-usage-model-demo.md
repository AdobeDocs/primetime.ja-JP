---
seo-title: 使用モデルのデモを有効にする
title: 使用モデルのデモを有効にする
uuid: 43930ebb-e936-4f48-990d-7ad19992e326
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---


# 使用モデルのデモ{#enable-the-usage-model-demo}を有効にします。

1. パッケージ化時にカスタムプロパティ`RI_UsageModelDemo=true`を指定します。

   Media Packagerコマンドラインツールを使用してコンテンツをパッケージ化する場合は、次のように入力します。

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>パッケージ化の際にオプションのデモモードをアクティブにしない場合、ライセンスサーバーは、処理する最初の有効なDRMポリシーに基づいてライセンスを発行します。

