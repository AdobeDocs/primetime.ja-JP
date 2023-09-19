---
description: トークンリクエストを適切な Expressplay トークンサーバーに送信することで、暗号化されたコンテンツの Expressplay トークンを生成できます。
title: Expressplay トークン
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 0%

---

# Expressplay トークン {#expressplay-tokens}

トークンリクエストを適切な Expressplay トークンサーバーに送信することで、暗号化されたコンテンツの Expressplay トークンを生成できます。

例として次の URL が挙げられます。

```
https://wv-gen.service.expressplay.com/hms/wv/
token?customerAuthenticator=<your expressplay customer authenticator>
&kid=fd1a706ac2b36002888f6d4a414333c3
&contentKey=5438b719bf47a2f5678237477db2f9e6
&securityLevel=1
&hdcpOutputControl=0
```

に指定されたコンテンツ暗号化キーストレージ ID または CEKSID `kid` パラメーターと、 `contentKey` パラメーターは、パッケージ化に使用するコンテンツ暗号化キーストレージ ID とコンテンツ暗号化キーに一致する必要があります。 次に、トークンサーバーの応答の例を示します。

```
https://wv.service.expressplay.com/hms/wv/rights/
?ExpressPlayToken=AQAAABIDKbgAAABQbt68jktab0YRY-r9mo6VP
 VqDDvkHq78x4V9_AyBUTtcNFHw5JtNKlKrMt-4HBdJ3Fopr7fqFSBp
 SJ4o-d8teAkUZUtW3Od5V-SHsCLnAlbFW84K71h2xNUiMAvRcUFBG3bjxMQ
```

次のいずれかを実行できます。

* 返された URL とクエリをライセンスサーバーの URL として使用するか、
* URL からクエリを取り出し、ExpressPlayToken を HTTPPOSTヘッダーとして別々に渡す
