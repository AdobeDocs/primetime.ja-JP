---
title: SWFアプリケーションの許可リストへの登録
description: SWFアプリケーションの許可リストへの登録
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# SWFアプリケーションの許可リストへの登録 {#swf-application-allowlisting}

SWF・アプリケーションを許可リストするには、次の 2 つの戦略のいずれかに従います。

* SWFの URL を指定できます。 これは非常に柔軟なアプローチです。特に、定期的にSWFを再構築する開発環境では、このアプローチが使用されます。
* HASH を指定できます。 これは、SWFの暗号化ダイジェスト値です。 このアプローチは、SWFが変更され、再構築されるとアプリケーション HASH が変更されるので、柔軟性が低くなります（ただし、より厳密です）。 この場合、以前の HASH にバインドされたすべてのコンテンツが新しいプレーヤーで再生に失敗し、再パッケージ化する必要があります。 The [!DNL PolicyManager.jar] 次の項目を指定すると、ツールは自動的にハッシュを計算します： [!DNL .swf] ファイル。

  一方、Flash/Adobe Media Server(FMS/AMS) 経由で Primetime DRM を使用している場合は、特定のSWFへのパスを指定できます。FMS/AMS は、FMS/AMS がストリーミングするコンテンツのパッケージ化に使用する DRM ポリシーに挿入するSWFを自動的にハッシュ化します。

詳しくは、 `policy.allowedSWFApplication.n` in *設定プロパティ* 」を参照してください。
