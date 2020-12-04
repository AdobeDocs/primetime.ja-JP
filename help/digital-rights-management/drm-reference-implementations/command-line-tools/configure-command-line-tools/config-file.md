---
description: 'null'
seo-description: 'null'
seo-title: コマンドラインツール設定ファイルについて
title: コマンドラインツール設定ファイルについて
uuid: 8220921f-1fe9-439c-8134-dc16c2e3601b
translation-type: tm+mt
source-git-commit: 0143d98185b9a63ef978aba18e2f3c8728333155
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# コマンドラインツール構成ファイルについて{#about-command-line-tools-configuration-files}

コマンドラインツールは、ツールを実行するディレクトリ内の[!DNL flashaccesstools.properties]を探します。 ただし、コマンドラインツールを実行する際に`-c`オプションを使用して、デフォルトの[!DNL flashaccesstools.properties]とは異なる場所を指定できます。 `-c`を使用して別の設定ファイルを指定することもできます。

コマンドラインツールの構成ファイルは、*Javaプロパティファイル*&#x200B;の形式を使用します。この形式には、次のルールが適用されます。

* 円記号を追加した円記号で円記号をエスケープします。

   例えば、Windowsマシンでは、[!DNL C:\credentials.pfx]ファイルを指定するには、[!DNL C:\\credentials.pfx]または`C:/credentials.pfx`と入力する必要があります。 Windowsネットワークサーバー上のファイルを指定するには、`\\\\server\\folder\\filename.pfx`と入力する必要があります。
* *Latin-1*&#x200B;文字のみを含めます。

   *Latin-1*&#x200B;以外の文字を使用するには、適切なUnicodeエスケープシーケンスを使用する必要があります。 必要に応じて、[!DNL native2ascii]ツール（Javaに付属）を設定ファイルのエントリに適用できます。
