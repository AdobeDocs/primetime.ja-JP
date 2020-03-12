---
description: 'null'
seo-description: 'null'
seo-title: コマンドラインツール設定ファイルについて
title: コマンドラインツール設定ファイルについて
uuid: 8220921f-1fe9-439c-8134-dc16c2e3601b
translation-type: tm+mt
source-git-commit: 0143d98185b9a63ef978aba18e2f3c8728333155

---


# コマンドラインツール設定ファイルについて{#about-command-line-tools-configuration-files}

コマンドラインツールは、ツールを実行 [!DNL flashaccesstools.properties] したディレクトリ内を検索します。 ただし、コマンドラインツー `-c` ルの実行時にこのオプションを使用して、デフォルトの別の場所を指定できま [!DNL flashaccesstools.properties]す。 を使用して、別の設定フ `-c` ァイルを指定することもできます。

コマンドラインツールの設定ファイルは、 *Javaプロパティファイルの形式を使用し* 、次のルールが適用されます。

* バックスラッシュを追加してエスケープします。

   例えば、Windowsマシンでは、ファイルを指定す [!DNL C:\credentials.pfx] るには、またはと入力する必要があ [!DNL C:\\credentials.pfx] ります `C:/credentials.pfx`。 Windowsネットワークサーバー上のファイルを指定するには、 `\\\\server\\folder\\filename.pfx`
* Latin-1文字 *のみ含め* ます。

   Latin-1以外の文字を使用す&#x200B;*るには* 、適切なUnicodeエスケープシーケンスを使用する必要があります。 オプションで、（Javaに付属の）ツ [!DNL native2ascii] ールを設定ファイルのエントリに適用することもできます。
