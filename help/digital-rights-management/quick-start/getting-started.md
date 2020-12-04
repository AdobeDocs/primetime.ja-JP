---
seo-title: はじめに
title: はじめに
uuid: 2002cf94-c8a7-4820-a560-6d9f7f33ee97
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---


# はじめに{#getting-started}

このドキュメントでは、プログレッシブダウンロードを使用してコンテンツを配布するAdobe PrimetimeDRMエコシステムのセットアップとデプロイをすばやく行う手順と、ライセンス配布のためのPrimetime DRM Server for Protected Streamingを行う手順を説明します。 各手順の詳細については、次のガイドを参照してください。

* *Primetime DRMサーバーを使用したコンテンツの保護*
* *保護されたストリーミングにPrimetime DRMサーバーを使用する*

保護されたストリーミング用のPrimetime DRMサーバーは、ソースコードを含まない最小の機能を持つサーバーです。 完全なJavaソースを持つ変更可能なサーバーについては、『Primetime DRM Reference Implementationsの使用&#x200B;*』ガイドを参照してください。*&#x200B;参照ライセンスサーバーを設定した場合は、*保護されたストリーミング用のPrimetime DRMサーバーのセットアップおよびデプロイ（ライセンスサーバー）*&#x200B;の手順に代わるものとなります。

## 前提条件{#prerequisites}

開始する前に、次のタスクを実行します。

* 2台のWindowsまたはLinuxコンピュータを入手する：

   * 1台のコンピュータがLicense Serverになります。
   * 1台のコンピューターがContent Serverになります。

* 両方のコンピューターに次のアプリケーションをインストールします。

   * Tomcat 6.0.18
   * Java 1.6

## 証明書の取得{#obtain-certificates}

SDKソフトウェアが配信された後、指定された会社証明書管理者は、Adobe PrimetimeDRM証明書登録プロセスを完了するように招待されます。 詳しくは、*Primetime DRM証明書登録ガイド*&#x200B;を参照してください。

1. 管理者は、証明書の要求者として動作する少なくとも1人を指定します。
1. 証明書の要求者は、秘密鍵とCSRを生成します。
1. 要求者は証明書要求を送信します。
1. 会社管理者がリクエストを承認します。
1. Adobe証明書管理者が送信を確認します。
1. 要求者は証明書を受け取り、証明書を秘密鍵と連結し、証明書をデプロイします。 を参照してください。

   証明書の展開について詳しくは、『*保護されたストリーミング用のAdobe PrimetimeDRMサーバーの展開*』ガイドを参照してください。
1. 手順3 ～ 6は、証明書の種類ごとに完了する必要があります。

   Primetime DRM実稼動バージョンの場合、リクエスターは、2年間有効なLicense Server、Packaging、Transportの証明書を個別にリクエストする必要があります。

   Primetime DRM評価版または体験版を使用するお客様は、1年/90日間有効な証明書を1つだけ必要とします。