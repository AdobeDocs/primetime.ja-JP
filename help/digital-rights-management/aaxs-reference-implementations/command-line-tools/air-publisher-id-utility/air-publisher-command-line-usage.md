---
title: コマンドラインの使用
description: コマンドラインの使用
copied-description: true
exl-id: 67056085-beb5-4f54-8962-369bc32d7907
source-git-commit: 79cab347d0daa01549fbf8a9b37bf0a91c14648e
workflow-type: tm+mt
source-wordcount: '75'
ht-degree: 0%

---

# コマンドラインの使用 {#command-line-usage}

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

* `signaturefile` アプリケーション内にあるAIRアプリケーションの signatures.xml ファイルへのパスを指定します。 [!DNL META-INF] directory

* `signingcert` AIRアプリケーションの署名に使用する証明書を指定します

>[!NOTE]
>
>iOSアプリケーションの Publisher ID を判断するには、 `-s` オプションを選択し、iOSアプリケーションへの署名に使用する証明書を指定します。 ***Adobe Primetimeは、アクセスで保護されたコンテンツを再生できるiOSアプリケーションを構築するために必要です***.
