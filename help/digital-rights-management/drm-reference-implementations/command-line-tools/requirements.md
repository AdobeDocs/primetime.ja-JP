---
title: コマンドラインツールの要件
description: コマンドラインツールの要件
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 0%

---


# コマンドラインツールの要件{#command-line-tools-requirements}

* Java 1.5以降。
* Adobeが発行するPackager、トランスポートおよびライセンスサーバーの資格情報（証明書とパスワード）。

   これらの資格情報は、ビデオファイルの暗号化と署名、ポリシーの更新と失効リストの署名、およびライセンスの事前生成に使用される資格情報です。

>[!NOTE]
>
>Javaのバグにより、コマンドラインで入力する引数（ファイル名、DRMポリシー名、説明など）は、オペレーティングシステムのデフォルトの文字セットの文字のみを使用できます。