---
title: 使用モデルのデモモードの設定
description: 使用モデルのデモモードの設定
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# 使用状況モデルのデモモードを設定{#configure-usage-model-demo-mode}

参照実装サーバーが使用モデルのデモのライセンスを発行する前に、4つの使用モデルのそれぞれに対してライセンスを生成する方法を指定するようにサーバーを設定する必要があります。 つまり、使用モデルごとにDRMポリシーを指定する必要があります。 リファレンスの実装には、[!DNL Reference Implementation/Server/Reference Implementation Server/resources/]ディレクトリに次のサンプルDRMポリシーが含まれています。

* `dto-policy.pol` - （ダウンロード先）
* `vod-policy.pol` - （レンタル/ビデオオンデマンド）
* `sub-policy.pol` - (購読)
* `ad-policy.pol`  — （広告による）

>[!NOTE]
>
>これらのサンプルポリシーを独自のDRMポリシーに置き換えることができます。

1. [!DNL flashaccess-refimpl.properties]で以下のプロパティを設定し、各使用モデルに適用するDRMポリシーを指定します。

   ```
   # DRM Policy file name for Download To Own usage 
   RefImpl.UsageModelDemo.Policy.DTO=dto-policy.pol 
   # DRM Policy file name for Rental usage 
   RefImpl.UsageModelDemo.Policy.VOD=vod-policy.pol 
   # DRM Policy file name for Subscription usage 
   RefImpl.UsageModelDemo.Policy.Subscribe=sub-policy.pol 
   # DRM Policy file name for Ad Supported (free) usage 
   RefImpl.UsageModelDemo.Policy.Free=ad-policy.pol
   ```

1. サンプルポリシーファイルを、[!DNL flashaccess-refimpl.properties]の`config.resourcesDirectory`プロパティで指定したディレクトリにコピーします。
