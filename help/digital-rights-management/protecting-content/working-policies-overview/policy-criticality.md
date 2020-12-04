---
seo-title: DRMポリシーの重要度
title: DRMポリシーの重要度
uuid: ddc03142-7acb-4a9f-a367-e34cfc5e78ba
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# DRMポリシーの重要度{#drm-policy-criticality}

DRMポリシーで新しい使用規則を適用する場合、古いライセンスサーバー用にパッケージ化されたコンテンツでこのDRMポリシーを使用する場合（したがって、新しい使用規則を正しく解釈しない場合）、古いライセンスサーバーの動作を指定する必要があります。 デフォルトでは、DRMポリシーの重要度は`true`に設定されています。

この設定は、指定したDRMポリシーを使用するライセンスを生成する前に、ライセンスサーバーがDRMポリシーのすべての部分を処理する必要があることを示します。 DRMポリシーの重要度が`false`に設定されている場合、古いライセンスサーバーは、DRMポリシーの中で正しく解釈できない部分を無視する可能性があります。 したがって、サーバーで生成されるライセンスには、新しい使用規則は含まれません。

SDKのバージョン2.0.2以降をサポートするPrimetime DRMサーバーは、DRMポリシーの重要度設定を受け入れます。
