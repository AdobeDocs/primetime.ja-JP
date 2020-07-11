---
seo-title: SWFアプリケーションでのリスト表示
title: SWFアプリケーションでのリスト表示
uuid: e3021ae9-54f4-4bcf-a274-515ae765f74b
translation-type: tm+mt
source-git-commit: 58bb3bedc5b0ac63afd96eb6101d9ad779e6deed
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# SWFアプリケーションでのリスト表示 {#swf-application-allowlisting}

SWFアプリケーションを許可リストするには、次の2つの方法のいずれかに従います。

* SWFへのURLを指定できます。 これは非常に柔軟なアプローチです。特に、SWFを定期的に再構築する開発環境では特に便利です。
* SWFハッシュを指定できます。 これは、SWFの暗号化ダイジェスト値です。 このアプローチは、アプリケーションが変更され再構築されるとSWF HASHが変更されるので、柔軟性に欠けます（ただし、より厳密に）。 この場合、以前のHASHに連結されたすべてのコンテンツは、新しいプレイヤーで再生できず、再パッケージする必要があります。 フ [!DNL PolicyManager.jar][!DNL .swf] ァイルを指定すると、自動的にハッシュが計算されます。

   一方、Flash/Adobe Media Server(FMS/AMS)を介してPrimetime DRMを使用している場合は、特定のSWFへのパスを指定すると、FMS/AMSが示すDRMポリシーに挿入するSWFがFMS/AMSによって自動的にハッシュされます。

詳し `policy.allowedSWFApplication.n` くは、 *設定プロパティの* 「」を参照してください。
