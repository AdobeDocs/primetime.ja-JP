---
title: Crossdomain ポリシーファイル
description: Crossdomain ポリシーファイル
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Crossdomain ポリシーファイル {#crossdomain-policy-file}

ライセンスサーバーがビデオ再生SWFとは異なるドメインでホストされている場合、SWFがライセンスサーバーからライセンスを要求できるように、クロスドメインポリシーファイル (crossdomain.xml) が必要です。 クロスドメインポリシーファイルは、サーバーがそのデータとドキュメントが他のドメインから提供されるSWFファイルで使用できることを示すための XML ファイルです。 ライセンスサーバーのクロスSWFポリシーファイルで指定されたドメインから提供されたドメインファイルは、そのライセンスサーバーのデータやアセットにアクセスできます。

Adobeでは、信頼されたドメインのみがライセンスサーバーにアクセスでき、Web サーバー上のライセンスサブディレクトリへのアクセスを制限することで、クロスドメインポリシーファイルを展開する際に、開発者はベストプラクティスに従うことをお勧めします。

クロスドメインポリシーファイルの詳細については、次の場所を参照してください。

* Web サイトの制御（ポリシーファイル）
* クロスドメインポリシーファイルの仕様： [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
