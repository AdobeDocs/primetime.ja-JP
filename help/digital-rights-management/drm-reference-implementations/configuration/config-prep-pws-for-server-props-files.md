---
description: 'null'
seo-description: 'null'
seo-title: サーバープロパティファイルのパスワードの準備
title: サーバープロパティファイルのパスワードの準備
uuid: 3e00ba9b-b692-4713-8306-5ab896461f2a
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# サーバープロパティファイルのパスワードの準備{#prepare-passwords-for-the-server-properties-files}

参照実装は、秘密鍵 `ScrambleUtil.class`証明書のパスワードをセキュリティで保護するクラスを提供します。

このツールを使用して、パスワードを暗号化してからファイルに含め [!DNL flashaccess-refimpl.properties] ます。

ツールを実行するには、AntスクリプトまたはJavaを使用できます。

このユーティリティは、暗号化されたパスワードを生成します。このパスワードはファイルにコピーする必要が [!DNL flashaccess-refimpl.properties] あります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>参照実装で提供されたを使用してエ `ScrambleUtil.class` ンコードされたパスワードは、保護されたストリーミング用のPrimetime DRMサーバーでは機能しません。
