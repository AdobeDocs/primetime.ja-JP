---
seo-title: Adobe Media Serverを使用する
title: Adobe Media Serverを使用する
uuid: 272b9919-6ae4-4adb-aab5-28b1f92aa9fe
translation-type: tm+mt
source-git-commit: 635e2893439c5459907c54d2c3bd86f58da0eec5

---


# Adobe Media Serverを使用する {#use-adobe-media-server}

一部のお客様は、既にAdobe Media Serverを使用しており、そのコンテンツ配信モデルを維持したいと考えている場合があります。 この場合、必要なPrimetime Cloud DRM固有のデータは、このキットに含まれる設定ファイルのいずれかから取得し、AMSのJIT(Just In Time)XML設定を入力できます。

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

