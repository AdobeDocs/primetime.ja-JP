---
title: サーバープロパティファイルのパスワードを準備する
description: サーバープロパティファイルのパスワードを準備する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# サーバープロパティファイルのパスワードを準備する{#prepare-passwords-for-the-server-properties-files}

リファレンス実装では、次の情報が提供されます。 `ScrambleUtil.class`：秘密鍵証明書のパスワードのセキュリティを確保するクラス。

このツールを使用して、パスワードを [!DNL flashaccess-refimpl.properties] ファイル。

ツールを実行するには、Ant スクリプトまたは Java を使用できます。

ユーティリティによって暗号化されたパスワードが生成され、次の場所にコピーする必要があります。 [!DNL flashaccess-refimpl.properties] ファイル。

>[!NOTE]
>
>を使用してエンコードされたパスワード `ScrambleUtil.class` で提供された参照実装は、保護されたストリーミング用の Primetime DRM サーバーでは機能しません。
