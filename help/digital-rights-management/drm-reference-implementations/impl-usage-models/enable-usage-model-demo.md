---
title: 使用モデルのデモを有効にする
description: 使用モデルのデモを有効にする
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
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

