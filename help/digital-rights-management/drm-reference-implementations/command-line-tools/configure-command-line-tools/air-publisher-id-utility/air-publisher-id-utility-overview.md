---
seo-title: 概要
title: 概要
uuid: f45c6b58-53c5-41e0-be3d-590231dd214a
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# AIR発行者IDユーティリティ {#air-publisher-id-utility}

AIRファイルを作成すると、AIR開発ツール(ADT)によって自動的に発行者IDが生成されます。 AIR発行者IDユーティリティ( [!DNL AdobePublisherIDUtility.jar])は、AIRアプリケーションの発行者IDを計算します。

発行者IDは、AIRファイルの作成に使用する証明書に対して一意です。 同じ証明書を複数のAIRアプリケーションで再利用する場合、すべてのAIRアプリケーションの発行者IDは同じになります。 リリース1.5.2に成功したAIRリリースでは、生成された発行者IDはファイルに追加されません。 したがって、AIRアプリケーションのホワイトリストを使用する場合は、このツールを使用して発行者IDを特定します。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>AIRホワイトリストの適用に使用される発行者IDは、アプリケーションの発行者がアプリケーションのファイルで指定する発行者IDとは異な [!DNL application.xml] ります。

## AIR発行者IDユーティリティのコマンドラインでの使用 {#air-publisher-id-utility-command-line-usage}

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
   * `signaturefile`*は、アプリケーションディレクトリ内にあるAIRアプリケ [!DNL signatures.xml] ーションのファイルへのパスを指定しま [!DNL META-INF] す。

* `signingcert` airアプリケーションへの署名に使用する証明書を指定します

>[!NOTE]
>
>Androidアプリケーションの発行者IDを特定するには、Androidアプリケーションパッケージ(APK) `-s` への署名に使用する証明書を指定するオプションを使用する必要があります。 Primetime DRMで保護されたコンテンツを再生できるAndroidアプリケーションを構築するには、Primetime DRMが必要です。