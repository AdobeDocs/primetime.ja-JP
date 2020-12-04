---
seo-title: パスとクラスパスの設定
title: パスとクラスパスの設定
uuid: cf10fafa-125e-450c-83ae-60b990dab6b5
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4
workflow-type: tm+mt
source-wordcount: '149'
ht-degree: 1%

---


# パスとクラスパスの設定{#configure-the-path-and-classpath}

[!DNL flashaccess.war]には[!DNL jsafeWithNative.jar]が含まれています。これはCrypto-Jライブラリです。 後者は、暗号化操作を実行するために追加のネイティブライブラリが必要です。

1. パス追加のネイティブ[!DNL jsafe]ライブラリ。

   * **Linux /  [!DNL libjsafe.so]  — を含むディレクトリ** はパス上に [!DNL libjsafe.so] 存在する必要があります（他のプラットフォームでもネイティブのCrypto-Jライブラリを利用できます）。例えば、`LD_LIBRARY_PATH`に[!DNL libjsafe.so]を設定します。

   * **Windows /  [!DNL jsafe.dll] - Windows** の対応するWindows/- [!DNL libjsafe.so] が適切 [!DNL jsafe.dll]です。
   これらのライブラリは、[!DNL thirdparty]ライブラリフォルダーにあります。
1. [!DNL adobe-flashaccess-certs] jarファイルの1つをクラスパスに配置します。

       このJARファイルは、WARファイルには含まれません。クラスパスに明示的に追加する必要があります。
   
   * 開発サーバー — [!DNL adobe-flashaccess-certs-prerelease.jar]のみを使用する必要があります。
   * 本番サーバ — [!DNL adobe-flashaccess- certs.jar]のみを使用

この配布物には[!DNL shared]フォルダーが含まれ、このフォルダーにはjarファイルと事前設定済みの[!DNL AdobeInitial.properties]ファイルの両方が含まれます。 Adobeでは、これらの項目を[!DNL catalina.properties]ファイルを介して`common.loader`に追加することをお勧めします。 例：

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```


