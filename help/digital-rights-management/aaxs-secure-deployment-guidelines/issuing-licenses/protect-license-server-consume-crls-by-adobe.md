---
seo-title: アドビが発行したCRLを使用
title: アドビが発行したCRLを使用
uuid: 43f65edb-0c96-46ab-b787-1b5f0b4b093e
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# アドビが発行したCRLを使用{#consume-crls-published-by-adobe}

SDKは、アドビが公開したCRLを定期的にダウンロードします。 これらのファイルへのアクセスをブロックしたり、これらのCRLを強制しないようにしてください。

SDKには、Adobe CRLを取得する際にエラーを無視する設定オプションがあります。 このオプションは、開発環境でのみ使用できます。 実稼働環境では、ライセンスサーバーがアドビからCRLを取得できる必要があります。 有効なCRLを取得できない場合は、エラーです。
