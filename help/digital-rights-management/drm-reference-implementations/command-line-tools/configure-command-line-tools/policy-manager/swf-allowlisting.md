---
title: SWFアプリケーションでのリスト表示
description: SWFアプリケーションでのリスト表示
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# SWFアプリケーションで{#swf-application-allowlisting}の一覧表示を許可

SWFアプリケーションを許可リストするには、次の2つの方法のいずれかに従います。

* SWFへのURLを指定できます。 これは非常に柔軟なアプローチです。特に、SWFを定期的に再構築する開発環境では特に便利です。
* SWFハッシュを指定できます。 これは、SWFの暗号化ダイジェスト値です。 このアプローチは、アプリケーションが変更され再構築されるとSWF HASHが変更されるので、柔軟性に欠けます（ただし、より厳密に）。 この場合、以前のHASHに連結されたすべてのコンテンツは、新しいプレーヤーで再生できず、再パッケージする必要があります。 [!DNL PolicyManager.jar]ファイルを指定すると、[!DNL .swf]ツールは自動的にハッシュを計算します。

   一方、Flash/Adobe Mediumサーバー(FMS/AMS)を介してPrimetime DRMを使用している場合は、特定のSWFへのパスを指定でき、FMS/AMSは、FMS/AMSがストリームするコンテンツのパッケージ化に使用するDRMポリシーにSWFを自動的に挿入します。

詳しくは、*設定プロパティ*&#x200B;の`policy.allowedSWFApplication.n`を参照してください。
