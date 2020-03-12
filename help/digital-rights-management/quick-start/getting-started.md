---
seo-title: はじめに
title: はじめに
uuid: 2002cf94-c8a7-4820-a560-6d9f7f33ee97
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# はじめに {#getting-started}

このドキュメントでは、プログレッシブダウンロードを使用してコンテンツを配信するAdobe Primetime DRMエコシステムの迅速なセットアップとデプロイの手順、およびライセンス配布用のPrimetime DRM Server for Protected Streamingの手順を説明します。 各手順の詳細については、次のガイドを参照してください。

* *Primetime DRMサーバーを使用したコンテンツの保護*
* *Primetime DRMサーバーを使用した保護されたストリーミング*

保護されたストリーミング用のPrimetime DRMサーバーは、ソースコードを含まない最小限の機能を持つサーバーです。 完全なJavaソースを持つ変更可能なサーバーについては、『Primetime DRMリファレ *ンスの実装の使用* 』ガイドを参照してください。 参照ライセンスサーバーを設定すると、「 *Setup」と「Deploy Primetime DRM Server for Protected Streaming(License Server)」の手順が置き換えられます* 。

## 前提条件 {#prerequisites}

開始する前に、次のタスクを実行します。

* 2台のWindowsまたはLinuxコンピュータを入手する：

   * 1台のコンピュータがライセンスサーバになります。
   * 1台のコンピューターがContent Serverになります。

* 両方のコンピューターに次のアプリケーションをインストールします。

   * Tomcat 6.0.18
   * Java 1.6

## 証明書の取得 {#obtain-certificates}

SDKソフトウェアが配信されると、指定された会社の証明書管理者に、Adobe Primetime DRM証明書の登録プロセスを完了するための招待が届きます。 詳しくは、Primetime DRM証明書登録ガ *イドを参照してください*。

1. 管理者は、証明書の要求者として少なくとも1人の個人を指定します。
1. 証明書の要求者は、秘密鍵とCSRを生成します。
1. 要求者は証明書要求を送信します。
1. 会社管理者がリクエストを承認します。
1. アドビの証明書管理者が送信を確認します。
1. 要求者は証明書を受け取り、証明書を秘密鍵と連結し、証明書をデプロイします。 を参照してください。

   証明書の配布について詳しくは、『Adobe Primetime DRMサーバーの *保護されたストリーミングへの配布* 』ガイドを参照してください。
1. 手順3 ～ 6は、各証明書の種類に対して完了する必要があります。

   Primetime DRM実稼働バージョンの場合、リクエスターは、2年間有効なLicense Server、Packaging、Transportの証明書を個別にリクエストする必要があります。

   Primetime DRM評価版または体験版を使用するお客様は、1年/90日間有効な証明書を1つだけ必要とします。