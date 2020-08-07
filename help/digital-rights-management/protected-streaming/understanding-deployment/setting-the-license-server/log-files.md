---
description: 保護されたストリーミングアプリケーション用のAdobe PrimetimeDRMサーバーによって生成されるログファイルは、LicenseServer.LogRootで指定されたディレクトリにあります。
seo-description: 保護されたストリーミングアプリケーション用のAdobe PrimetimeDRMサーバーによって生成されるログファイルは、LicenseServer.LogRootで指定されたディレクトリにあります。
seo-title: ログファイル
title: ログファイル
uuid: 4498fe60-65af-4f99-8f9b-e85013d0c9e9
translation-type: tm+mt
source-git-commit: 1b9792a10ad606b99b6639799ac2aacb707b2af5
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---


# ログファイル{#log-files}

保護されたストリーミングアプリケーション用のAdobe PrimetimeDRMサーバーによって生成されるログファイルは、LicenseServer.LogRootで指定されたディレクトリにあります。

>[!NOTE]
>
>サーバーの実行中に現在のログファイルを削除または移動した場合、ログファイルは再作成できない場合があります。 したがって、一部のログ情報は削除される場合があります。

## ログディレクトリ構造 {#section_F490A483D60145ADBC21038914C39203}

ログディレクトリは使いやすいように構造化されています。 ログディレクトリの構造は次のとおりです。

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

グローバルログファイル [!DNL flashaccess-global.log]は、LicenseServer.LogRootにあり *ます*。 ログには、サーバーが初期化された際に、Adobe PrimetimeDRM Java SDKまたはログメッセージで生成されたログメッセージが含まれる場合があります。

## パーティションログファイル {#section_5660137CD6AA40519E72A4315534846B}

パーティションログファイル [!DNL flashaccess-partition.log]は、 [!DNL <LicenseServer.LogRoot>/flashaccesserver] ディレクトリ内にあります。 これには、ライセンス要求の処理中に生成されたログメッセージが含まれます。

## テナントログファイル {#section_F0257CC0831647F18A746B4F02E3E910}

各テナントのテナントログファイル [!DNL flashaccess-tenant.log]は、 [!DNL &lt;LicenseServer.LogRoot>/flashaccessserver/tenants/にあります。<tenantname>]. テナントログには、このテナント用に生成された各ライセンスを説明する監査情報が含まれます。
