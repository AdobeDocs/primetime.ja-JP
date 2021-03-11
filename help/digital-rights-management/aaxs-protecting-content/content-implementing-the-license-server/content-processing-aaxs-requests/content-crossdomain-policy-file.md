---
title: クロスドメインポリシーファイル
description: クロスドメインポリシーファイル
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# クロスドメインポリシーファイル{#crossdomain-policy-file}

ライセンスサーバーがビデオ再生SWFとは異なるドメインでホストされている場合は、SWFがライセンスサーバーからライセンスを要求できるように、クロスドメインポリシーファイル(crossdomain.xml)が必要です。 クロスドメインポリシーファイルはXMLファイルで、サーバーがそのデータとドキュメントを他のドメインから提供されたSWFファイルで使用できることを示す手段を提供します。 ライセンスサーバーのクロスドメインポリシーファイルで指定されたドメインから提供されるSWFファイルは、そのライセンスサーバーのデータまたはアセットにアクセスできます。

Adobeでは、クロスドメインポリシーファイルを展開する際に、ベストプラクティスに従って、信頼されたドメインだけがライセンスサーバーにアクセスでき、Webサーバー上のライセンスサブディレクトリへのアクセスを制限することを推奨します。

クロスドメインポリシーファイルの詳細については、次の場所を参照してください。

* Webサイトコントロール（ポリシーファイル）
* クロスドメインポリシーファイルの指定：[https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

