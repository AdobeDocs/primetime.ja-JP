---
title: DRMポリシーの重要度
description: DRMポリシーの重要度
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '155'
ht-degree: 0%

---


# DRMポリシーの重要度{#drm-policy-criticality}

DRMポリシーで新しい使用規則を適用する場合、古いライセンスサーバー用にパッケージ化されたコンテンツでこのDRMポリシーを使用する場合（したがって、新しい使用規則を正しく解釈しない場合）、古いライセンスサーバーの動作を指定する必要があります。 デフォルトでは、DRMポリシーの重要度は`true`に設定されています。

この設定は、指定したDRMポリシーを使用するライセンスを生成する前に、ライセンスサーバーがDRMポリシーのすべての部分を処理する必要があることを示します。 DRMポリシーの重要度が`false`に設定されている場合、古いライセンスサーバーは、DRMポリシーの中で正しく解釈できない部分を無視する可能性があります。 したがって、サーバーで生成されるライセンスには、新しい使用規則は含まれません。

SDKのバージョン2.0.2以降をサポートするPrimetime DRMサーバーは、DRMポリシーの重要度設定を受け入れます。
