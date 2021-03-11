---
title: 概要
description: 概要
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---


# AIRパブリッシャーIDユーティリティ{#air-publisher-id-utility}

AIRファイルを構築すると、AIR Developer Tool(ADT)によって自動的に発行者IDが生成されます。 AIR発行者IDユーティリティ([!DNL AdobePublisherIDUtility.jar])は、AIRアプリケーションの発行者IDを計算します。

発行者IDは、AIRファイルの作成に使用する証明書に固有です。 同じ証明書を複数のAIRアプリケーションに再利用する場合、すべてのAIRアプリケーションで同じ発行者IDが使用されます。 リリース1.5.2に成功したAIRリリースでは、生成された発行者IDはファイルに追加されません。 したがって、AIRアプリケーション許可リストを使用する場合は、このツールを使用して発行者IDを決定します。

>[!NOTE]
>
>AIR許可リストの適用に使用される発行者IDは、アプリケーションの発行者がアプリケーションの[!DNL application.xml]ファイルで指定する発行者IDとは異なります。

## AIR Publisher IDユーティリティのコマンドラインでの使用{#air-publisher-id-utility-command-line-usage}

```
java -jar AdobePublisherIDUtility.jar 
<i class="+ topic ph hi-d="" i "="">
 <i class="+ topic ph hi-d="" i "="">
  signaturefile 
  java -jar AdobePublisherIDUtility.jar -s 
  <i class="+ topic ph hi-d="" i "="">
    signingcert
  </i class="+ topic>
 </i class="+ topic>
</i class="+ topic>
```

* 
   * `signaturefile`*は、applicationsディレクトリ内にあるAIRアプリケーションの [!DNL signatures.xml] ファイルへのパスを指定し [!DNL META-INF] ます

* `signingcert` は、AIRアプリケーションへの署名に使用する証明書を指定します

>[!NOTE]
>
>Androidアプリケーションの発行者IDを特定するには、`-s`オプションを使用して、Androidアプリケーションパッケージ(APK)の署名に使用する証明書を指定する必要があります。 Primetime DRMで保護されたコンテンツを再生できるAndroidアプリケーションを作成するには、Primetime DRMが必要です。