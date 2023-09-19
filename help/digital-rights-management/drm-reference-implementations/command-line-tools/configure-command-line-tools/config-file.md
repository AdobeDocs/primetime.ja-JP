---
title: コマンドラインツールの設定ファイルについて
description: コマンドラインツールの設定ファイルについて
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 0%

---

# コマンドラインツールの設定ファイルについて{#about-command-line-tools-configuration-files}

コマンドラインツールは、 [!DNL flashaccesstools.properties] をクリックします。 ただし、 `-c` オプションを使用して、既定の [!DNL flashaccesstools.properties]. また、 `-c` 別の設定ファイルを指定する場合。

コマンドラインツールの設定ファイルでは、 *Java プロパティファイル* 形式を使用します。この形式には、次のルールが適用されます。

* バックスラッシュを追加のバックスラッシュでエスケープします。

  例えば、Windows マシンでは、 [!DNL C:\credentials.pfx] ファイルを次のように入力する必要があります： [!DNL C:\\credentials.pfx] または `C:/credentials.pfx`. Windows ネットワークサーバー上でファイルを指定するには、次を入力する必要があります。 `\\\\server\\folder\\filename.pfx`
* 次のみを含む： *Latin-1* 文字。

  次以外の&#x200B;*Latin-1* 文字を使用する場合は、適切な Unicode エスケープシーケンスを使用する必要があります。 必要に応じて、 [!DNL native2ascii] ツール（Java に含まれる）を設定ファイルのエントリに追加します。
