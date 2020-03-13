---
seo-title: SWFアプリのホワイトリスト
title: SWFアプリのホワイトリスト
uuid: e3021ae9-54f4-4bcf-a274-515ae765f74b
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# SWFアプリのホワイトリスト{#swf-application-whitelisting}

SWFアプリケーションをホワイトリストに登録するには、次の2つの方法のいずれかに従います。

* SWFのURLを指定できます。 これは非常に柔軟なアプローチで、特にSWFを定期的に再構築する開発環境では特にそうです。
* SWFハッシュを指定できます。 これは、SWFの暗号化ダイジェスト値です。 このアプローチは、アプリケーションが変更され再構築される際にSWF HASHが変更されるので、柔軟性が低くなります（ただし、より厳密です）。 この場合、前のHASHにバインドされたすべてのコンテンツは、新しいプレーヤーで再生に失敗し、再パッケージ化する必要があります。 ファイル [!DNL PolicyManager.jar] を指定すると、ツールは自動的にハッシュを計算 [!DNL .swf] します。

   一方、Flash/Adobe Media Server(FMS/AMS)を介してPrimetime DRMを使用している場合は、特定のSWFへのパスを指定でき、FMS/AMSは、FMS/AMSによってストリームされるコンテンツのパッケージ化に使用されるDRMポリシーに挿入するSWFを自動的にハッシュ化します。

詳しくは、 `policy.allowedSWFApplication.n` 設定プ *ロパティの* 「」を参照してください。
