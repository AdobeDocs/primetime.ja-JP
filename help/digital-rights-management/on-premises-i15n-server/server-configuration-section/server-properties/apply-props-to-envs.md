---
description: '環境を反映するようにサーバーのプロパティを設定する必要があります。 これを行うには、次のいずれかを使用します '
title: サーバー環境へのプロパティの適用
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# サーバー環境にプロパティを適用{#apply-properties-to-server-environments}

環境を反映するようにサーバーのプロパティを設定する必要があります。 これを行うには、次のいずれかを使用します。

* [!DNL flashaccess-i15n.properties]  — 各 [!DNL .war] ファイルに含まれるサンプル

* [!DNL AdobeInitial.properties] - DVDの [!DNL /shared] フォルダーにあるサンプル

   このファイルを使用して、WARファイルで設定されたプロパティを次のように上書きできます。

   1. [!DNL AdobeInitial.properties]内に上書きプロパティ値を設定します
   1. クラスパスに[!DNL AdobeInitial.properties]を配置します。

   >[!NOTE]
   >
   >[!DNL AdobeInitial.properties]ファイルは、[!DNL flashaccess-i15n.properties]ファイルで行った以前のプロパティ設定を失うことなく、アプリケーションのWARファイルを更新できるので、Adobeではファイルを使用することをお勧めします。

* Java Systemプロパティのメカニズム。

次の特定のサーバー環境に個々のプロパティを適用できます。

* *開発*
* *ステージング*
* *実稼働環境*

この機能を使用すると、すべてのサーバー環境に同じWARファイルを使用できます。 特定の環境にプロパティを適用するには、2つのアンダースコア文字(&#39;`__`&#39;)と次の環境コードの1つをプロパティ&#x200B;*name*&#x200B;に追加します。

    * `DEV`
    * `STAGE`
    * `PROD`

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

例えば、実稼働サーバーとステージングサーバーのログレベルを`INFO`に設定し、開発サーバーのログレベルを`DEBUG`に設定するには、次のように記述します。

```
log.Level=INFO  
log.Level__DEV=DEBUG 
```

サーバーでは、次のプロパティの検索順序が使用されます。

1. `propertyname_environment` in  [!DNL AdobeInitial.properties]

1. `propertyname_environment` in  [!DNL flashaccess-15n.properties]

1. `propertyname_environment` Java Systemプロパティ
1. `propertyname` in  [!DNL AdobeInitial.properties]

1. `propertyname` in  [!DNL flashaccess-15n.properties]

1. `propertyname` Java Systemプロパティ

>[!NOTE]
>
>サーバーを起動する際に、Java Systemプロパティとしてサーバーの環境名を指定する必要があります。 例えば、[!DNL catalina.bat]でTomcatを起動する場合、`CATALINA_OPTS`環境変数を次のように設定します。
>-DENVIRONMENT_NAME=[開発環境 | STAGE | PROD ]
