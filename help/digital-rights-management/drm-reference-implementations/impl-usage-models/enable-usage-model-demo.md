---
title: 使用状況モデルのデモを有効にする
description: 使用状況モデルのデモを有効にする
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# 使用状況モデルのデモを有効にする{#enable-the-usage-model-demo}

1. カスタムプロパティを指定する `RI_UsageModelDemo=true` パッケージ時に。

   Media Packager のコマンドラインツールを使用してコンテンツをパッケージ化する場合は、次のように入力します。

   ```
   java -jar AdobeMediaPackager.jar [<i>source_file</i>] [<i>dest_file</i>] -k RI_UsageModelDemo=true
   ```

>[!NOTE]
>
>パッケージ化時にオプションのデモモードを有効化しない場合、ライセンスサーバーは処理する最初の有効な DRM ポリシーに基づいてライセンスを発行します。
