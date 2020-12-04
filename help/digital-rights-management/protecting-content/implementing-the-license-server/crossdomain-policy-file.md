---
seo-title: Crossdomain DRMポリシーファイル
title: Crossdomain DRMポリシーファイル
uuid: cb91a85a-1825-4fd7-a25c-880cdbd5c8b8
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# クロスドメインDRMポリシーファイル{#crossdomain-drm-policy-file}

ライセンスサーバーがビデオ再生SWFとは異なるドメインでホストされている場合は、SWFがライセンスサーバーからライセンスを要求できるようにするために、クロスドメインDRMポリシーファイル([!DNL crossdomain.xml])が必要です。 クロスドメインDRMポリシーファイルはXMLファイルで表されます。XMLファイルを使用すると、サーバーは、他のドメインから提供されたSWFファイルでそのデータとドキュメントを使用できることを示すことができます。 ライセンスサーバーのクロスドメインDRMポリシーファイルで指定されたドメインから提供されるSWFファイルは、そのライセンスサーバーのデータまたはアセットにアクセスできます。

Adobeでは、クロスドメインポリシーファイルを展開する際に、ベストプラクティスに従って、信頼されたドメインだけがライセンスサーバーにアクセスでき、Webサーバー上のライセンスサブディレクトリへのアクセスを制限することを推奨します。

クロスドメインDRMポリシーファイルについて詳しくは、次の場所を参照してください。

* Webサイトコントロール（DRMポリシーファイル）
* クロスドメインDRMポリシーファイルの仕様：[https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

