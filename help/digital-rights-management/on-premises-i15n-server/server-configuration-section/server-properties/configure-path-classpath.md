---
seo-title: パスとクラスパスの設定
title: パスとクラスパスの設定
uuid: cf10fafa-125e-450c-83ae-60b990dab6b5
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# パスとクラスパスの設定{#configure-the-path-and-classpath}

には、Crypto-J [!DNL flashaccess.war][!DNL jsafeWithNative.jar]ライブラリであるを含めます。 後者は、暗号化操作を実行するために追加のネイティブライブラリが必要です。

1. パスにネイティブラ [!DNL jsafe] イブラリを追加します。

   * **Linux /[!DNL libjsafe.so]— を含むディレ**[!DNL libjsafe.so] クトリはパス上に存在する必要があります（他のプラットフォームでもネイティブのCrypto-Jライブラリを使用できます）。 例えば、をonに設 [!DNL libjsafe.so] 定します `LD_LIBRARY_PATH`。

   * **Windows /[!DNL jsafe.dll]-** Windows上での対応が適 [!DNL libjsafe.so] 切です [!DNL jsafe.dll]。
   これらのライブラリは、ライブラリフォルダー内で使 [!DNL thirdparty] 用できます。
1. jarファイルの1つをク [!DNL adobe-flashaccess-certs] ラスパスに配置します。

       このJARファイルはWARファイルには含まれません。クラスパスに明示的に追加する必要があります。
   
   * 開発サーバー — 使用のみ [!DNL adobe-flashaccess-certs-prerelease.jar]。
   * 実稼働サーバー — [!DNL adobe-flashaccess- certs.jar]

配布には、jarファ [!DNL shared] イルと事前設定ファイルの両方を含むフォルダーが含まれ [!DNL AdobeInitial.properties] ます。 これらの項目は、ファイルを通じてに追加す `common.loader` ることをお勧め [!DNL catalina.properties] します。 例：

```
common.loader=<Any Pre-Existing Values>,${catalina.home}/shared/classes,${catalina.home}/shared/lib/*.jar
```


