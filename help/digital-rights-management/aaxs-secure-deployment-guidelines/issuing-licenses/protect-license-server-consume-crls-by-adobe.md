---
title: Adobeで公開された CRL を使用
description: Adobeで公開された CRL を使用
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '83'
ht-degree: 0%

---

# Adobeで公開された CRL を使用{#consume-crls-published-by-adobe}

SDK は、Adobeが公開した CRL を定期的にダウンロードします。 これらのファイルへのアクセスをブロックしたり、これらの CRL の適用を防いだりしないでください。

SDK には、エラー CRL の取得時にエラーを無視するAdobeオプションがあります。 このオプションは、開発環境でのみ使用できます。 実稼動環境では、ライセンスサーバーがAdobeから CRL を取得できる必要があります。 有効な CRL を取得できなかった場合は、エラーです。
