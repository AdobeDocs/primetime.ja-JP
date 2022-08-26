---
title: 登録レコードを返す
description: 登録レコードを返す
source-git-commit: 4c3a0dd56b4ef99ac8c57cfde61f792088b0ff4d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# 登録レコードを返す {#return-registration-record}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。


## REST API エンドポイント {#clientless-endpoints}

&lt;reggie_fqdn>:

* 実稼動 — [api.auth.adobe.com](http://api.auth.adobe.com/)
* ステージング — [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

&lt;sp_fqdn>:

* 実稼動 — [api.auth.adobe.com](http://api.auth.adobe.com/)
* ステージング — [api.auth-staging.adobe.com](http://api.auth-staging.adobe.com/)

 </br>
 

## 説明 {#description}

登録コード UUID、登録コード、ハッシュ化されたデバイス ID を含む登録コードレコードを返します。 

 

<div>


| エンドポイント | 呼び出し済み  </br>作成者 | 入力   </br>パラメーター | HTTP  </br>メソッド | 応答 | HTTP  </br>応答 |
| --- | --- | --- | --- | --- | --- |
| &lt;reggie_fqdn>;/regige/v1/{requestorId}/regcode/{registrationCode}</br></br>例：</br></br>&lt;reggie_fqdn>/reggie/v1/sampleRequestorId/regcode/TJJCFK?format=xml | ストリーミングアプリ</br></br>または</br></br>プログラマーサービス | 1.要求者  </br>    （パスコンポーネント）</br>2.  登録コード  </br>    （パスコンポーネント） | GET | 登録コードと情報を含む XML または JSON。 以下のスキーマとサンプルを参照してください。 | 200 |

{style=&quot;table-layout:auto&quot;}

</br>

| 入力パラメーター | 説明 |
| --- | --- |
| 要求者 | この操作が有効な ProgrammerRequestorId。 |
| 登録コード | ストリーミングデバイスに表示される登録コード値（認証フローに入力される値）です。 |

</br>

## 応答 XML スキーマ {#response-xml-schema}

### 登録コード XSD

```XML
    <?xml version="1.0" encoding="UTF-8"?>
    <xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns="model.mvc.reggie.pass.adobe.com"
            targetNamespace="model.mvc.reggie.pass.adobe.com"
            attributeFormDefault="unqualified"
            elementFormDefault="unqualified">
        <xs:element name="regcode">
            <xs:complexType>
                <xs:all>
                    <xs:element name="id" type="xs:string" />
                    <xs:element name="code" type="xs:string" />
                    <xs:element name="requestor" type="xs:string" minOccurs="1" maxOccurs="1"/>
                    <xs:element name="mvpd" type="xs:string" minOccurs="1" maxOccurs="1"/
                    <xs:element name="generated" type="xs:long" />
                    <xs:element name="expires" type="xs:long" />
                    <xs:element name="info" type="infoType" maxOccurs="1"/>
                </xs:all>
            </xs:complexType>
        </xs:element>
        <xs:complexType name="infoType">
            <xs:all>
                <xs:element name="deviceId" type="xs:base64Binary" minOccurs="1" maxOccurs="1"/>
                <xs:element name="deviceType" type="xs:string" minOccurs="0" maxOccurs="1"/>
                <xs:element name="deviceUser" type="xs:string" minOccurs="0" maxOccurs="1"/>
                <xs:element name="appId" type="xs:string" minOccurs="0" maxOccurs="1"/>
                <xs:element name="appVersion" type="xs:string" minOccurs="0" maxOccurs="1"/>
                <xs:element name="registrationURL" type="xs:anyURI" minOccurs="0" maxOccurs="1"/>
            </xs:all>
        </xs:complexType>
    </xs:schema>
```

| エレメント名 | 説明 |
| --- | --- |
| id | 登録コードサービスで生成された UUID |
| コード | 登録コードサービスによって生成された登録コード |
| 要求者 | 要求者 ID |
| mvpd | MVPD ID |
| 生成済み | 登録コード作成タイムスタンプ (1970 年 1 月 1 日 (GMT) からのミリ秒単位 ) |
| 有効期限 | 登録コードの有効期限が切れたときのタイムスタンプ (1970 年 1 月 1 日 (GMT) からのミリ秒単位 ) |
| deviceId | 一意のデバイス ID（または XSTS トークン） |
| deviceType | デバイスタイプ |
| deviceUser | デバイスにログインしたユーザー |
| appId | アプリケーション ID |
| appVersion | アプリケーションのバージョン |
| registrationURL | エンドユーザーに表示されるログイン Web アプリの URL |

{style=&quot;table-layout:auto&quot;}

### レスポンスのサンプル {#sample-response}

```XML
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
    <ns2:regcode xmlns:ns2="model.mvc.reggie.pass.adobe.com">
        <id>678f9fea-a1cafec8-1ff0-4a26-8564-f6cd020acf13</id>
        <code>TJJCFK</code>
        <requestor>sampleRequestorId</requestor>
        <mvpd>sampleMvpdId</mvpd>
        <generated>1348039846647</generated>
        <expires>1348043446647</expires>
        <info>
            <deviceId>dGhpc0lkQUR1bW15RGV2aWNlSWQ=</deviceId>
            <deviceType>xbox</deviceType>
            <deviceUser>JD</deviceUser>
            <appId>2345</appId>
            <appVersion>2.0</appVersion>
            <registrationURL>http://loginwebapp.com</registrationURL>
        </info>
    </ns2:regcode>
```

[REST API リファレンスに戻る](http://tve.helpdocsonline.com/rest-api-reference)