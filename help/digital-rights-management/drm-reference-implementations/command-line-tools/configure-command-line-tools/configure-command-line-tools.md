---
title: コマンドラインツールの設定と実行
description: コマンドラインツールの設定と実行
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '109'
ht-degree: 0%

---


# コマンドラインツールを構成して実行{#configure-and-run-the-command-line-tools}

コマンドラインツールには関連するプロパティがあり、このプロパティの値を[!DNL flashaccesstools.properties] **&#x200B;に設定してからツールを実行する必要があります。 コマンドラインツールには、コマンドラインからプロパティ値を指定する機能もあります。 コマンドラインで指定した値は、[!DNL flashaccesstools.properties]から指定した値よりも優先されます。

使用する対応するコマンドラインツールを有効にするには、[!DNL flashaccesstools.properties]の次のセクションの設定を変更する必要があります。

* **Media Packagerのプロパティ** - ( [!DNL AdobePackager.jar]対象)

* **Policy Updateリストマネージャーと失効リストマネージャーのプロパティ** - ( [!DNL AdobePolicyUpdateListManager.jar] および [!DNL AdobeRevocationListManager.jar])

* **Policy Managerのプロパティ** - ( [!DNL AdobePolicyManager.jar]対象)

* **License Generatorのプロパティ** - ( [!DNL AdobeLicenseGenerator.jar]対象)