---
seo-title: コマンドラインの使用
title: コマンドラインの使用
uuid: 54b1e867-c6cc-4355-b8e6-a7ec910bd33d
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

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

* 
   * `signaturefile`*は、アプリケーションディレクトリ内にあるAIRアプリケーションのsignatures.xmlファイルへのパスを指定しま [!DNL META-INF] す。

* `signingcert` airアプリケーションへの署名に使用する証明書を指定します

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>iOSアプリケーションの発行者IDを特定するには、このオプションを使 `-s` 用し、iOSアプリケーションの署名に使用する証明書を指定します。 ***Adobe Primetimeは、アクセス保護されたコンテンツを再生できるiOSアプリケーションを構築するために必要です***。

