---
description: 'null'
seo-description: 'null'
seo-title: サーバープロパティファイルのパスワードの準備
title: サーバープロパティファイルのパスワードの準備
uuid: 3e00ba9b-b692-4713-8306-5ab896461f2a
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '103'
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
