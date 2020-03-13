---
description: 'null'
seo-description: 'null'
seo-title: 使用状況モデルのデモモードの設定
title: 使用状況モデルのデモモードの設定
uuid: f818c7fc-e88f-4fa4-926e-08a1337b28d3
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 使用状況モデルのデモモードの設定{#configure-usage-model-demo-mode}

参照実装サーバーが使用モデルのデモのライセンスを発行する前に、4つの使用モデルのそれぞれに対してライセンスを生成する方法を指定するようにサーバーを設定する必要があります。 つまり、各使用モデルに対してDRMポリシーを指定する必要があります。 参照の実装には、次のサンプルDRMポリシーがディレクトリに含まれ [!DNL Reference Implementation/Server/Reference Implementation Server/resources/] ています。

* `dto-policy.pol` - （ダウンロードして所有）
* `vod-policy.pol` - （レンタル/ビデオオンデマンド）
* `sub-policy.pol` - （購読）
* `ad-policy.pol`  — （広告が出資）

>[!NOTE]
>
>これらのサンプルポリシーを独自のDRMポリシーに置き換えることができます。

1. 各使用モデルに適用 [!DNL flashaccess-refimpl.properties] するDRMポリシーを指定するには、次のプロパティをに設定します。

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

1. サンプルポリシーファイルを、のプロパティで指定したディレクトリ `config.resourcesDirectory` にコピーしま [!DNL flashaccess-refimpl.properties]す。
