---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---


# コマンドラインの使用{#command-line-usage}

ツールを実行するには、次の構文を使用します。

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

* `signaturefile` は、applications [!DNL META-INF] ディレクトリ内にあるAIRアプリケーションのsignatures.xmlファイルへのパスを指定します。

* `signingcert` は、AIRアプリケーションへの署名に使用する証明書を指定します

>[!NOTE]
>
>iOSアプリケーションの発行者IDを特定するには、`-s`オプションを使用し、iOSアプリケーションの署名に使用する証明書を指定します。 ***Adobe Primetimeは、アクセスで保護されたコンテンツを再生できるiOSアプリケーションを構築する必要があります***。

