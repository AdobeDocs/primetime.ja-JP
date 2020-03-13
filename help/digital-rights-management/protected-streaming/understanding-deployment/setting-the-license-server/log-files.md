---
description: Adobe Primetime DRM Serverで保護されたストリーミングアプリケーション用に生成されたログファイルは、LicenseServer.LogRootで指定されたディレクトリにあります。
seo-description: Adobe Primetime DRM Serverで保護されたストリーミングアプリケーション用に生成されたログファイルは、LicenseServer.LogRootで指定されたディレクトリにあります。
seo-title: ログファイル
title: ログファイル
uuid: 4498fe60-65af-4f99-8f9b-e85013d0c9e9
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# ログファイル{#log-files}

Adobe Primetime DRM Serverで保護されたストリーミングアプリケーション用に生成されたログファイルは、LicenseServer.LogRootで指定されたディレクトリにあります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>サーバーの実行中に現在のログファイルが削除または移動された場合、ログファイルは再作成できない場合があります。 そのため、一部のログ情報は削除される場合があります。

## ログディレクトリの構造 {#section_F490A483D60145ADBC21038914C39203}

ログディレクトリは、使いやすさを考慮した構造になっています。 ログディレクトリの構造は次のとおりです。

```
<i class="+ topic ph hi-d="" i "="">
 LicenseServer.LogRoot/ 
 flashaccess-global.log 
     flashaccessserver/ 
         flashaccess-partition.log 
         tenants/ 
             
 <i class="+ topic ph hi-d="" i "="">
  tenantname/ 
                  flashaccess-tenant.log
 </i class="+ topic>
</i class="+ topic>
```

## グローバルログファイル {#section_1CFA90748142439C9F3BE380969539DA}

グローバルログファイル [!DNL flashaccess-global.log]は、 *LicenseServer.LogRootにあります*。 ログには、Adobe Primetime DRM Java SDKを使用したログメッセージや、サーバーの初期化時に生成されたログメッセージが含まれる場合があります。

## パーティションログファイル {#section_5660137CD6AA40519E72A4315534846B}

パーティション・ログ・ファ [!DNL flashaccess-partition.log]イルは、ディレクトリ内にあ [!DNL <LicenseServer.LogRoot>/flashaccesserver] ります。 ライセンス要求の処理中に生成されたログメッセージが含まれます。

## テナントログファイル {#section_F0257CC0831647F18A746B4F02E3E910}

各テナントのテナントログフ [!DNL flashaccess-tenant.log]ァイルは、 [!DNL &lt;LicenseServer.LogRoot>/flashaccesserver/tenants/にあります。<tenantname>]. テナントログには、このテナントに対して生成された各ライセンスを説明する監査情報が含まれます。
