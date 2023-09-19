---
title: コマンドラインツールの要件
description: コマンドラインツールの要件
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '79'
ht-degree: 0%

---

# コマンドラインツールの要件 {#command-line-tools-requirements}

* Java 1.5 以降。
* Packager が発行した Packager、トランスポート、およびライセンスサーバーの資格情報 ( 証明書とAdobe)。

  これらは、ビデオファイルの暗号化と署名、ポリシーの更新リストと失効リストへの署名、およびライセンスの事前生成に使用される資格情報です。

>[!NOTE]
>
>Java のバグのため、コマンドラインに入力した引数（ファイル名、DRM ポリシー名、説明など）は、オペレーティングシステムのデフォルト文字セットの文字のみを使用できます。
