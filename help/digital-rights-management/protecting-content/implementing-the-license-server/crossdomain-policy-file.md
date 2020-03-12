---
seo-title: クロスドメインDRMポリシーファイル
title: クロスドメインDRMポリシーファイル
uuid: cb91a85a-1825-4fd7-a25c-880cdbd5c8b8
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# クロスドメインDRMポリシーファイル {#crossdomain-drm-policy-file}

ライセンスサーバーがビデオ再生SWFとは異なるドメインでホストされている場合は、SWFがライセンスサーバーのライセンスを要求できるようにするために、クロスドメインDRMポリシーファイル( [!DNL crossdomain.xml])が必要です。 クロスドメインDRMポリシーファイルはXMLファイルで表されます。このファイルを使用すると、サーバーは、他のドメインから提供されたSWFファイルでそのデータとドキュメントを使用できることを示すことができます。 ライセンスサーバーのクロスドメインDRMポリシーファイルで指定されたドメインから提供されるSWFファイルは、そのライセンスサーバーのデータまたはアセットにアクセスできます。

アドビでは、クロスドメインポリシーファイルを展開する際に、信頼されたドメインのみがライセンスサーバーにアクセスでき、Webサーバー上のライセンスサブディレクトリへのアクセスを制限することで、開発者にベストプラクティスに従うことを推奨します。

クロスドメインDRMポリシーファイルについて詳しくは、次の場所を参照してください。

* Webサイトのコントロール（DRMポリシーファイル）
* クロスドメインDRMポリシーファイルの仕様：https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html [](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

