---
seo-title: クロスドメインポリシーファイル
title: クロスドメインポリシーファイル
uuid: fc05aa5e-6fbd-445f-a22a-f795d5a0b3ad
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
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

