---
description: 環境を反映するようにサーバーのプロパティを設定する必要があります。 次のいずれかを使用してこれを実行できます。
title: サーバー環境へのプロパティの適用
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# サーバー環境へのプロパティの適用{#apply-properties-to-server-environments}

環境を反映するようにサーバーのプロパティを設定する必要があります。 これをおこなうには、次のいずれかを使用します。

* [!DNL flashaccess-i15n.properties] ・各サンプルに含まれるサンプル [!DNL .war] ファイル

* [!DNL AdobeInitial.properties]  — 内のサンプル [!DNL /shared] DVD 上のフォルダ

  このファイルを使用して、WAR ファイルで設定されたプロパティを次のように上書きできます。

   1. 上書きするプロパティ値をに設定します。 [!DNL AdobeInitial.properties]
   1. 場所 [!DNL AdobeInitial.properties] クラスパスの

  >[!NOTE]
  >
  >Adobeでは、 [!DNL AdobeInitial.properties] ファイルを更新すると、以前に設定したプロパティが失われる恐れがなく、アプリケーションの WAR ファイルを更新できます。 [!DNL flashaccess-i15n.properties] ファイル。

* Java System プロパティーのメカニズム。

次の特定のサーバー環境に個々のプロパティを適用できます。

* *開発*
* *ステージング*
* *実稼動*

この機能を使用すると、すべてのサーバ環境で同じ WAR ファイルを使用できます。 特定の環境にプロパティを適用するには、2 つのアンダースコア文字 (&#39; `__`&#39;) プロパティに次のいずれかの環境コードを追加します。 *名前*:

* `DEV`
* `STAGE`
* `PROD`

<!--<a id="example_A7A58E3EE8DA4114B4F7A9EEB69D50CA"></a>-->

例えば、ログレベルをに設定するには、次のようにします。 `INFO` 実稼動サーバーとステージングサーバーの `DEBUG` 開発サーバーの場合：

```
log.Level=INFO  
log.Level__DEV=DEBUG 
```

サーバーは、次のプロパティの検索順序を使用します。

1. `propertyname_environment` in [!DNL AdobeInitial.properties]

1. `propertyname_environment` in [!DNL flashaccess-15n.properties]

1. `propertyname_environment` （Java システムのプロパティ）
1. `propertyname` in [!DNL AdobeInitial.properties]

1. `propertyname` in [!DNL flashaccess-15n.properties]

1. `propertyname` （Java システムのプロパティ）

>[!NOTE]
>
>サーバーの起動時に、サーバーの環境名を Java System プロパティとして指定する必要があります。 例えば、Tomcat を [!DNL catalina.bat]を設定し、 `CATALINA_OPTS` 環境変数の内容を次に示します。
>-DENVIRONMENT_NAME=[開発 | STAGE | PROD]
