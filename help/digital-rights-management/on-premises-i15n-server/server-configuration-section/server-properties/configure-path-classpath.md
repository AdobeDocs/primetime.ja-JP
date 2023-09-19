---
title: パスとクラスパスの設定
description: パスとクラスパスの設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 0%

---

# パスとクラスパスの設定{#configure-the-path-and-classpath}

The [!DNL flashaccess.war] 次を含む [!DNL jsafeWithNative.jar]:Crypto-J ライブラリ。 後者の場合は、暗号化操作を実行するために追加のネイティブライブラリが必要です。

1. ネイティブの追加 [!DNL jsafe] ライブラリをパスに追加します。

   * **Linux / [!DNL libjsafe.so] -** を含むディレクトリ [!DNL libjsafe.so] はパス上に存在する必要があります（他のプラットフォームでもネイティブの Crypto-J ライブラリを使用できます）。 例えば、 [!DNL libjsafe.so] オン `LD_LIBRARY_PATH`.

   * **Windows / [!DNL jsafe.dll] -** Windows 上でのに対応する [!DNL libjsafe.so] が適切である [!DNL jsafe.dll].

   これらのライブラリは、 [!DNL thirdparty] ライブラリフォルダー。
1. 次のいずれかを配置： [!DNL adobe-flashaccess-certs] クラスパスの jar ファイル。

       この JAR ファイルは WAR ファイルに含まれていません。クラスパスに明示的に追加する必要があります。
   
   * 開発サーバー — 使用する必要があるのは [!DNL adobe-flashaccess-certs-prerelease.jar].
   * 実稼動サーバー — 使用する必要があるのは [!DNL adobe-flashaccess- certs.jar]

この配分には、 [!DNL shared] jar ファイルと事前設定済みの [!DNL AdobeInitial.properties] ファイル。 Adobeでは、次の項目を `common.loader` 経由 [!DNL catalina.properties] ファイル。 例：

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```
