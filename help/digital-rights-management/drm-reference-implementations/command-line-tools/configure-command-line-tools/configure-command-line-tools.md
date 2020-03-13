---
seo-title: コマンドラインツールの設定と実行
title: コマンドラインツールの設定と実行
uuid: b65f8621-54fa-4927-b2f4-d2fd60350fc1
translation-type: tm+mt
source-git-commit: 19e7c941b3337c3b4d37f0b6a1350aac2ad8a0cc

---


# コマンドラインツールの設定と実行 {#configure-and-run-the-command-line-tools}

コマンドラインツールには関連するプロパティがあり、ツールを実行する前に [!DNL flashaccesstools.properties] で値を *設定* する必要があります。 コマンドラインツールの一部では、コマンドラインからプロパティ値を指定することもできます。 コマンドラインで指定した値は、指定した値よりも優先されま [!DNL flashaccesstools.properties]す。

使用する対応するコマンドラインツールを有効にする [!DNL flashaccesstools.properties] には、の次のセクションの設定を変更する必要があります。

* **Media Packagerのプロパティ** - ( [!DNL AdobePackager.jar]対象)

* **Policy Update List ManagerとRevocation List Manager Properties** - ( [!DNL AdobePolicyUpdateListManager.jar] および [!DNL AdobeRevocationListManager.jar])

* **Policy Managerのプロパティ** - ( [!DNL AdobePolicyManager.jar]対象)

* **License Generatorのプロパティ** - ( [!DNL AdobeLicenseGenerator.jar]用)