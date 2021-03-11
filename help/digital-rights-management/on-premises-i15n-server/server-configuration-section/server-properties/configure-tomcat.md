---
title: Tomcatの設定
description: Tomcatの設定
copied-description: true
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---


# Tomcatを設定{#configure-tomcat}

個別化サーバーで、Tomcatの[!DNL conf/server.xml]ファイルを変更し、アクセスログに追加情報を含めます。 この情報は、レポートの目的に使用できます。

1. [!DNL server.xml]内の`AccessLogValve`の設定を探し、次に示すようにパターンを変更します。

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` は、 `x-forwarded-for` ヘッダーの値を記録します。Apacheリバースプロキシを使用してTomcatサーバーに要求を転送する場合、このヘッダーには元のクライアントのIPアドレスが含まれますが、`%h`はApacheサーバーのIPアドレスを記録します。 `%{request-id}r` は、個別化アプリケーションログに含まれるリクエストIDに対応するリクエスト識別子を記録します。

1. [!DNL conf/server.xml]を編集し、`unpackwars`プロパティをfalseに設定します。

   個別化サーバーとキー生成サーバーの両方で、[!DNL conf/server.xml]を編集し、`unpackwars`プロパティを`false`に設定することをお勧めします。 そうしないと、WARを更新する際に、パック解除されたWARフォルダも削除する必要がある場合があります。

>[!NOTE]
>
>今後のDRMクライアントでは、Tomcatで使用可能なCORS(接触チャネル間のリソース共有)フィルターを有効にし、設定する必要があります。 現在、この要件を持つDRMクライアントはありません。

