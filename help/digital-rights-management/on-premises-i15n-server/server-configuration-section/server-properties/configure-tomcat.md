---
title: Tomcat の設定
description: Tomcat の設定
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Tomcat の設定{#configure-tomcat}

個別化サーバーで、Tomcat の [!DNL conf/server.xml] ファイルに追加の情報を記録します。 この情報は、レポート目的で使用できます。

1. の設定を見つけます。 `AccessLogValve` in [!DNL server.xml] 次に示すように、パターンを変更します。

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` は、 `x-forwarded-for` ヘッダー。 Apache のリバースプロキシを使用して要求を Tomcat サーバーに転送する場合、このヘッダーには元のクライアントの IP アドレスが含まれますが、 `%h` は Apache サーバーの IP アドレスを記録します。 `%{request-id}r` は、個別化アプリケーションログに含まれるリクエスト ID に対応するリクエスト識別子を記録します。

1. 編集 [!DNL conf/server.xml] をクリックし、 `unpackwars` プロパティを false に設定します。

   個別化サーバーと鍵生成サーバーの両方で、 [!DNL conf/server.xml] をクリックし、 `unpackwars` プロパティを `false`. WAR を更新する場合は、パック化されていない WAR フォルダも削除する必要がある場合があります。

>[!NOTE]
>
>今後の DRM クライアントでは、Tomcat で使用可能な CORS（クロスオリジンリソース共有）フィルターを有効にして設定する必要があります。 現在、この要件を満たす DRM クライアントはありません。
