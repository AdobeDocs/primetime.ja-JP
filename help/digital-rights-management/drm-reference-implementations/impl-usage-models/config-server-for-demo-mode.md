---
title: 使用状況モデルのデモモードを設定する
description: 使用状況モデルのデモモードを設定する
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# 使用状況モデルのデモモードを設定する{#configure-usage-model-demo-mode}

参照実装サーバーが使用モデルデモのライセンスを発行する前に、サーバーを設定して、4 つの使用モデルのそれぞれに対してライセンスを生成する方法を指定する必要があります。 つまり、各使用モデルに DRM ポリシーを指定する必要があります。 参照実装には、次のサンプル DRM ポリシーがに含まれています。 [!DNL Reference Implementation/Server/Reference Implementation Server/resources/] ディレクトリ：

* `dto-policy.pol` - （ダウンロード先）
* `vod-policy.pol` - （レンタル/ビデオオンデマンド）
* `sub-policy.pol` - （購読）
* `ad-policy.pol` - （広告資金）

>[!NOTE]
>
>これらのサンプルポリシーを独自の DRM ポリシーに置き換えることができます。

1. 次のプロパティをに設定します。 [!DNL flashaccess-refimpl.properties] 各使用モデルに適用する DRM ポリシーを指定するには、次の手順を実行します。

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

1. サンプルポリシーファイルを、 `config.resourcesDirectory` プロパティ： [!DNL flashaccess-refimpl.properties].
