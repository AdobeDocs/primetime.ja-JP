---
seo-title: クロスドメインポリシーファイル
title: クロスドメインポリシーファイル
uuid: fc05aa5e-6fbd-445f-a22a-f795d5a0b3ad
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# クロスドメインポリシーファイル {#crossdomain-policy-file}

ライセンスサーバーがビデオ再生SWFとは異なるドメインでホストされている場合は、SWFがライセンスサーバーのライセンスを要求できるように、クロスドメインポリシーファイル(crossdomain.xml)が必要です。 クロスドメインポリシーファイルはXMLファイルで、サーバーのデータとドキュメントが他のドメインから提供されたSWFファイルで使用可能であることを示す手段を提供します。 ライセンスサーバーのクロスドメインポリシーファイルで指定されたドメインから提供されるSWFファイルは、そのライセンスサーバーのデータまたはアセットにアクセスできます。

アドビでは、クロスドメインポリシーファイルを展開する際に、信頼されたドメインのみがライセンスサーバーにアクセスでき、Webサーバー上のライセンスサブディレクトリへのアクセスを制限することで、開発者にベストプラクティスに従うことを推奨します。

クロスドメインポリシーファイルについて詳しくは、次の場所を参照してください。

* Webサイトのコントロール（ポリシーファイル）
* クロスドメインポリシーファイルの指定：https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html [](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)

