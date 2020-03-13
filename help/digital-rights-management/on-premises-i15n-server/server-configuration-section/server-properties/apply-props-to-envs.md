---
description: '環境を反映するようにサーバーのプロパティを設定する必要があります。 これは、次のいずれかを使用して行うことができます。 '
seo-description: '環境を反映するようにサーバーのプロパティを設定する必要があります。 これは、次のいずれかを使用して行うことができます。 '
seo-title: サーバー環境へのプロパティの適用
title: サーバー環境へのプロパティの適用
uuid: a1ee0d6c-b5e7-4689-b7c8-b155176faf1c
translation-type: tm+mt
source-git-commit: d8e4c39c297d69b154baf0b4d67cf09b5cf0a9d4

---


# サーバー環境へのプロパティの適用{#apply-properties-to-server-environments}

環境を反映するようにサーバーのプロパティを設定する必要があります。 これは、次のいずれかを使用して行うことができます。

* [!DNL flashaccess-i15n.properties]  — 各ファイルに含まれるサンプ [!DNL .war] ル

* [!DNL AdobeInitial.properties] - DVD上のフォルダーに [!DNL /shared] あるサンプル

   このファイルを使用して、WARファイルで設定されたプロパティを次のように上書きできます。

   1. 上書きプロパティの値を [!DNL AdobeInitial.properties]
   1. クラス [!DNL AdobeInitial.properties] パスに配置します。
   >[!NOTE]
   >
   >このファイルを使用すると、以前にファイルで行ったプロパティ設定が失われることなく、アプリケーションのWARファイルを更新できるので、アドビではこのファイルを使用することをお勧めし [!DNL AdobeInitial.properties][!DNL flashaccess-i15n.properties] ます。

* Java Systemプロパティメカニズム。

次の特定のサーバー環境に個々のプロパティを適用できます。

* *開発*
* *ステージング*
* *実稼働環境*

この機能を使用すると、すべてのサーバー環境で同じWARファイルを使用できます。 特定の環境にプロパティを適用するには、2つのアンダースコア文字(&#39; `__`&#39;)と次の環境コードの1つをプロパティ名に追加 *します*。

    * `DEV`
    * `STAGE`
    * `PROD`

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

例えば、実稼働サーバーとステージングサ `INFO` ーバー、および開発サーバーのログレベルを `DEBUG` に設定するには、次のようにします。

```
log.Level=INFO  
log.Level__DEV=DEBUG 
```

サーバーは、次のプロパティの検索順序を使用します。

1. `propertyname_environment` in [!DNL AdobeInitial.properties]

1. `propertyname_environment` in [!DNL flashaccess-15n.properties]

1. `propertyname_environment` Java Systemプロパティ
1. `propertyname` in [!DNL AdobeInitial.properties]

1. `propertyname` in [!DNL flashaccess-15n.properties]

1. `propertyname` Java Systemプロパティ

>[!NOTE]
>
>サーバーの起動時に、サーバーの環境名をJava Systemプロパティとして指定する必要があります。 例えば、でTomcatを起動する場合、次のよ [!DNL catalina.bat]うに環境変数 `CATALINA_OPTS` を設定します。
>-DENVIRONMENT_NAME=[ DEV| STAGE| PROD ]
