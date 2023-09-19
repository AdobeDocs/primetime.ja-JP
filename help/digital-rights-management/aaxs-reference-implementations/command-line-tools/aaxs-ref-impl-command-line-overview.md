---
title: コンテンツのパッケージ化と失効リストの作成を行うコマンドラインツール
description: コンテンツのパッケージ化と失効リストの作成を行うコマンドラインツール
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# コンテンツのパッケージ化と失効リストの作成を行うコマンドラインツール {#command-line-tools-for-packaging-content-revocation-lists}

リファレンス実装には、次のコマンドラインツールが含まれています。

* Policy Manager：ポリシーを作成および管理するためのツール
* Policy Update List Manager：ポリシー更新リストを作成および表示するためのツールです。
* 失効リストマネージャー：失効リストを作成および表示するためのツールです。
* Media Packager：暗号化された FLV および F4V ファイルを作成するためのツール
* AIR Publisher ID
* UtilityLicense Generator
* ライセンス埋め込み機能

## 要件 {#requirements}

リファレンス実装で使用可能なコマンドラインツールを使用する際の要件は次のとおりです。

* すべてのコマンドラインツールには Java 1.5 以降が必要です。
* Adobeが発行する Packager と License Server の資格情報（証明書とパスワード）。 ビデオファイルの暗号化と署名、ポリシーの更新リストと失効リストへの署名、およびライセンスの事前生成を行うための資格情報が必要です。

>[!NOTE]
>
>Java のバグのため、コマンドラインで使用される引数（ファイル名、ポリシー名、説明など）は、オペレーティングシステムのデフォルトの文字セットの文字のみを使用する必要があります。

## 設定ファイル {#configuration-file}

一部のコマンドラインツールでは、ポリシーの適用と暗号化ファイルに使用するツールの情報を含む構成ファイルが必要です。

デフォルトの設定ファイルは、 [!DNL flashaccesstools.properties]. このディレクトリは作業ディレクトリ内にあります。つまり、ツールを実行するディレクトリです（コマンドラインツールのインストールを参照）。 各ツールには、オプション ( `-c`) をクリックすると、デフォルトのを使用しない場合に、使用する設定ファイルを指定できます。

設定ファイルでは、Java プロパティのファイル形式を使用します。 いずれかのプロパティの値に特殊文字が含まれる場合は、次の制限事項に注意してください。

* バックスラッシュを追加のバックスラッシュでエスケープします。 例えば、 [!DNL C:\credentials.pfx] ファイルを次のように指定します。 [!DNL C:\\credentials.pfx] または `C:/credentials.pfx`. ネットワークサーバー上のファイルを指定するには、次を指定します。 `\\\\server\\folder\\filename.pfx`.
* 設定ファイルには、Latin-1 文字のみを含めることができます。 Latin-1 以外の文字を使用する必要がある場合は、適切な Unicode エスケープシーケンスを使用します ( オプションで、 [!DNL native2ascii] Java に付属するツール ) を使用します。

ツールを実行する前に、設定ファイルのプロパティの値を設定します。 一部のコマンドラインツールでは、コマンドラインまたは設定ファイルを使用して、一部のオプションの値を設定できます。 この場合、コマンドラインで設定された値は、設定ファイル内の値よりも優先されます。

## コマンドラインツールのインストール  {#installing-the-command-line-tools}

必要なファイルを [!DNL \Reference Implementation\Command Line Tools] DVD 上のディレクトリ ( デフォルトの [!DNL flashaccesstools.properties] 設定ファイル、および [!DNL libs] ディレクトリ。ツールの JAR ファイルが格納されます。

The [!DNL samples] ディレクトリには、AdobeAccess SDK API の使用方法を示す Java ソースファイルのサンプルが含まれています。 サンプルをビルドして実行するには、 [!DNL build-samples.xml] Ant スクリプト。
