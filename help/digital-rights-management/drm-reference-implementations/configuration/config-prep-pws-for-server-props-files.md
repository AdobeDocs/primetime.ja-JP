---
title: サーバープロパティファイルのパスワードの準備
description: サーバープロパティファイルのパスワードの準備
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---


# サーバーのプロパティファイル{#prepare-passwords-for-the-server-properties-files}のパスワードを準備します

参照実装は、`ScrambleUtil.class`を提供します。これは、秘密鍵証明書のパスワードをセキュリティで保証するクラスです。

パスワードを[!DNL flashaccess-refimpl.properties]ファイルに含める前に、このツールを使用してパスワードを暗号化します。

ツールを実行するには、AntスクリプトまたはJavaスクリプトを使用できます。

ユーティリティは暗号化されたパスワードを生成します。このパスワードは[!DNL flashaccess-refimpl.properties]ファイルにコピーする必要があります。

>[!NOTE]
>
>参照実装で指定された`ScrambleUtil.class`でエンコードされたパスワードは、保護ストリーミング用のPrimetime DRMサーバーでは機能しません。
