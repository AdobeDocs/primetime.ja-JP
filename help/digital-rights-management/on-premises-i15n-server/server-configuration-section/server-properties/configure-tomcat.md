---
seo-title: Tomcatの設定
title: Tomcatの設定
uuid: 5f23aa33-29d7-4b41-87a4-59dc5b433de4
translation-type: tm+mt
source-git-commit: 7e8df034035fe465fbe403949ef828e7811ced2e

---


# Tomcatの設定{#configure-tomcat}

個別化サーバーで、Tomcatのファイルを変更し、 [!DNL conf/server.xml] アクセスログに追加情報を含めます。 この情報は、レポートの目的に使用できます。

1. の設定を探し、次のよ `AccessLogValve` うに [!DNL server.xml] パターンを変更します。

   ```
   <Valve className="org.apache.catalina.valves.AccessLogValve" 
   directory="logs" prefix="localhost_access_log." suffix=".txt" 
   pattern="%h %{x-forwarded-for}i %l %u %t &quot;%r&quot; %s %b 
   %{request-id}r" resolveHosts="false"/>
   ```

   `%{x-forwarded-for}i` はヘッダの値を記録し `x-forwarded-for` ます。 Apacheリバースプロキシを使用してTomcatサーバーに要求を転送する場合、このヘッダーには元のクライアントのIPアドレスが含まれますが、Apacheサーバーの `%h` IPアドレスは記録されます。 `%{request-id}r` は、個別化アプリケーションログに含まれるリクエストIDに対応するリクエスト識別子を記録します。

1. プロパテ [!DNL conf/server.xml] ィを編集し、false `unpackwars` に設定します。

   個別化サーバーとキー生成サーバーの両方の場合、プロパティを編集してに設定す [!DNL conf/server.xml] ることをお勧 `unpackwars` めしま `false`す。 そうしないと、WARを更新する際に、パック解除されたWARフォルダもクリーンアップする必要がある場合があります。

>[!NOTE]
>
>今後のDRMクライアントでは、Tomcatで使用可能なCORS(Cross-Origin Resource Sharing)フィルターを有効にし、設定する必要が生じます。 現在、この要件を持つDRMクライアントはありません。

