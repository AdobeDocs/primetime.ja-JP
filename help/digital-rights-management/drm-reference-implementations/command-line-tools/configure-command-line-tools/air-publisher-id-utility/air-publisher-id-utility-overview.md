---
title: 概要
description: 概要
copied-description: true
exl-id: 07f2ef0b-c6aa-4574-a3ae-18685a090cf2
source-git-commit: a1fc67b708f3d5821532d3827639adbadf15f6b4
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# AIR Publisher ID ユーティリティ {#air-publisher-id-utility}

AIRファイルを作成すると、AIR Developer Tool(ADT) によって Publisher ID が自動的に生成されます。 AIR Publisher ID ユーティリティ ( [!DNL AdobePublisherIDUtility.jar]) は、AIRアプリケーションの Publisher ID を計算します。

Publisher ID は、AIRファイルの作成に使用する証明書に対して一意です。 複数のAIRアプリケーションで同じ証明書を再利用する場合、すべてのAIRアプリケーションの Publisher ID は同じになります。 リリース 1.5.2 に成功したAIRリリースでは、生成された Publisher ID がファイルに追加されません。 したがって、AIRアプリケーション許可リストを使用する予定がある場合は、このツールを使用して Publisher ID を特定します。

>[!NOTE]
>
>AIR許可リストの適用に使用される Publisher ID は、アプリケーションの Publisher ID とは異なります。 [!DNL application.xml] ファイル。

## AIR Publisher ID ユーティリティのコマンドラインの使用 {#air-publisher-id-utility-command-line-usage}

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

* `signaturefile` AIRアプリケーションの [!DNL signatures.xml] ファイル，アプリケーション内にある [!DNL META-INF] directory

* `signingcert` AIRアプリケーションの署名に使用する証明書を指定します

>[!NOTE]
>
>Android アプリケーションの発行者 ID を判断するには、 `-s` オプションを使用して、Android アプリケーションパッケージ (APK) への署名に使用する証明書を指定します。 Primetime DRM で保護されたコンテンツを再生できる Android アプリケーションを構築するには、Primetime DRM が必要です。
