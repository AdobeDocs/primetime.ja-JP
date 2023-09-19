---
description: 保護されたストリーミング用のAdobe Access Serverには、グローバル設定ファイル (flashaccess-global.xml) と各テナント用のテナント設定ファイル (flashaccess-tenant.xml) の 2 種類の設定ファイルが必要です。
title: 設定ディレクトリの構造
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '137'
ht-degree: 0%

---

# ライセンスサーバの設定ファイルと設定ディレクトリの構造 {#configuration-directory-structure}

保護されたストリーミング用のAdobe Access Serverには、グローバル設定ファイル (flashaccess-global.xml) と、各テナント用のテナント設定ファイル (flashaccess-tenant.xml) の 2 種類の設定ファイルが必要です。

設定ファイルを編集した後、Adobeでは、Adobe Access Server for Protected Streaming に付属のユーティリティを使用して、ファイルの形式が正しいことを確認することをお勧めします。 詳しくは、[設定バリデーター](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/configuration-validator.md)&quot;.

設定ファイル内のクリアテキストでパスワードを使用できないようにするには、グローバルおよびテナントの設定ファイルで指定されているすべてのパスワードを暗号化する必要があります。 パスワードの暗号化の詳細については、「[パスワードスクランブラ](../../aaxs-protected-streaming/aaxs-protected-streaming-utilities/password-scrambler.md)&quot;.

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
