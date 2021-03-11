---
title: 証明書の要求（要求者）
description: 証明書の要求（要求者）
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '118'
ht-degree: 0%

---


# 証明書の要求（要求元）{#request-a-certificate-requester}

1. 証明書の登録サイトにログオンします。

   証明書を要求するユーザーは、要求者である必要があります。

1. 「Request」タブで、証明書の種類（License Server、PackagerまたはTransport）を選択します。

   >[!NOTE]
   >
   >このオプションは、評価版および体験版SDKのバージョンには表示されません。 これらのSDKバージョンでは、1つの証明書を使用します。

1. 次のいずれかの操作を行います。

   * CSRファイルをアップロードします。
   * CSRからCSR情報をコピーし、フォームに貼り付けます。

      >[!NOTE]
      >
      >CSR情報をコピーするには、開始タグ`(-----BEGIN CERTIFICATE REQUEST-----)`と終了タグ`(-----END CERTIFICATE REQUEST-----)`の間のテキスト（開始タグを含まない）を選択します。

1. **[!UICONTROL Submit Request]**&#x200B;ボタンをクリックします。

   レビュー用の電子メールがアカウントおよびセカンダリ管理者に送信されます。 依頼者はCCdです。

