---
description: 適切なExpressplayトークンサーバーにトークンリクエストを送信することで、暗号化されたコンテンツに対するExpressplayトークンを生成できます。
title: Expressplayトークン
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---


# Expressplayトークン{#expressplay-tokens}

適切なExpressplayトークンサーバーにトークンリクエストを送信することで、暗号化されたコンテンツに対するExpressplayトークンを生成できます。

例えば、次のURLがあります。

```
https://wv-gen.service.expressplay.com/hms/wv/
token?customerAuthenticator=<your expressplay customer authenticator>
&kid=fd1a706ac2b36002888f6d4a414333c3
&contentKey=5438b719bf47a2f5678237477db2f9e6
&securityLevel=1
&hdcpOutputControl=0
```

`kid`パラメーターに指定するコンテンツ暗号化キーストレージIDまたはCEKSIDと、`contentKey`パラメーターに指定するコンテンツ暗号化キーまたはCEKは、パッケージ化に使用するコンテンツ暗号化キーストレージIDとコンテンツ暗号化キーと一致する必要があります。 次に、トークンサーバーの応答例を示します。

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

その後、

* 返されたURLとクエリをライセンスサーバーのURLとして使用するか、
* URLからクエリを取り出し、HTTPPOSTヘッダーとして別々にExpressPlayTokenを渡す