---
description: 保護ストリーミング用Adobe Access Serverでは、グローバル設定ファイル(flashaccess-global.xml)と各テナント用のテナント設定ファイル(flashaccess-tenant.xml)の2種類の設定ファイルが必要です。
seo-description: 保護ストリーミング用Adobe Access Serverでは、グローバル設定ファイル(flashaccess-global.xml)と各テナント用のテナント設定ファイル(flashaccess-tenant.xml)の2種類の設定ファイルが必要です。
seo-title: 設定ディレクトリの構造
title: 設定ディレクトリの構造
uuid: c6cfc734-6b7c-4502-9bdb-c7aaca156e0e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '167'
ht-degree: 0%

---


# ライセンスサーバ構成ファイルと構成ディレクトリ構造{#configuration-directory-structure}

保護ストリーミング用のAdobe Access Serverには、次の2種類の設定ファイルが必要です。グローバル設定ファイル(flashaccess-global.xml)と各テナントのテナント設定ファイル(flashaccess-tenant.xml)。

設定ファイルを編集した後、Adobeでは、保護ストリーミング用のAdobe Access Serverに付属のユーティリティを使用して、ファイルが適切な形式であることを確認することをお勧めします。 詳しくは、「[構成バリデーター](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)」を参照してください。

構成ファイル内のパスワードをクリアテキストで使用できないようにするには、グローバル構成ファイルとテナント構成ファイルで指定されているすべてのパスワードを暗号化する必要があります。 パスワードの暗号化の詳細については、「[パスワードスクランブラ](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)」を参照してください。

設定ディレクトリの構造は次のとおりです。

```
<i class="+ topic ph hi-d="" i "="">
  LicenseServer.ConfigRoot/  
  flashaccess-global.xml  
  pkcs11.cfg (optional)  
  flashaccessserver/  
   libs/ (optional)  
   tenants/  
     
 <i class="+ topic ph hi-d="" i "="">
   tenantname/  
      flashaccess-tenant.xml  
       
  <i class="+ topic ph hi-d="" i "="">
    credential.pfx (optional)  
        
   <i class="+ topic ph hi-d="" i "="">
     packagercert.cer (optional) 
   </i class="+ topic> 
  </i class="+ topic> 
 </i class="+ topic> 
</i class="+ topic>
```

