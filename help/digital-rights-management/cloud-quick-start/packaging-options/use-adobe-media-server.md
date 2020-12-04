---
seo-title: Adobeメディアサーバを使用
title: Adobeメディアサーバを使用
uuid: 272b9919-6ae4-4adb-aab5-28b1f92aa9fe
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5
workflow-type: tm+mt
source-wordcount: '66'
ht-degree: 3%

---


# Adobeメディアサーバを使用{#use-adobe-media-server}

一部のお客様は、既にAdobeメディアサーバーを使用しており、そのコンテンツ配信モデルを維持したいと考えている場合があります。 この場合、必要なPrimetime Cloud DRM固有のデータは、このキットに含まれる設定ファイルのいずれかから収集して、AMSのJIT(Just In Time)XML設定に入力できます。

例：

```xml
<?xml version="1.0"?>
<Application>
  <HDS>
    <HLS>
      <Encryption enabled="true" protection-scheme="AdobeAccessV4">
        <AdobeAccessV4>
          <ContentID>SampleVideo</ContentID>
          <CommonKeyPath>common-key.bin</CommonKeyPath>
          <LicenseServerURL>
            https://access.adobeprimetime.com/flashaccessserver/axs_prod
          </LicenseServerURL>
          <KeyServerURL>
            https://access.adobeprimetime.com:443/faxsks/axs_prod/key
          </KeyServerURL>
          <TransportCertPath>cert/Cloud DRM-transport.cer</TransportCertPath>
          <LicenseServerCertPath>cert/Cloud DRM-license.cer</LicenseServerCertPath>
          <PackagerCredentialPath>cert-from-adobe.pfx</PackagerCredentialPath>
          <PackagerCredentialPwd>pass-for-cert-from-adobe</PackagerCredentialPwd>
          <PolicyPath>policy_ios_localkeyserver.pol</PolicyPath>
        </AdobeAccessV4>
      </Encryption>
    </HLS>
  </HDS>
</Application>
```

