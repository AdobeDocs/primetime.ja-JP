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


# サーバープロパティファイルのパスワードの準備{#prepare-passwords-for-the-server-properties-files}

参照実装は、秘密鍵証明書 `ScrambleUtil.class`のパスワードをセキュリティで保証するクラスを提供します。

このツールを使用して、パスワードを [!DNL flashaccess-refimpl.properties] ファイルに含める前に暗号化します。

ツールを実行するには、AntスクリプトまたはJavaスクリプトを使用できます。

暗号化されたパスワードはユーティリティによって生成され、 [!DNL flashaccess-refimpl.properties] ファイルにコピーする必要があります。

>[!NOTE]
>
>参照実装で指定されたパスワードを使用 `ScrambleUtil.class` してエンコードされたパスワードは、保護されたストリーミング用のPrimetime DRMサーバーでは機能しません。
