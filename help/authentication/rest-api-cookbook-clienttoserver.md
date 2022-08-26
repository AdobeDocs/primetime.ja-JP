---
title: REST API クックブック（クライアント/サーバー間）
description: Rest API クックブッククライアントからサーバーへ。
source-git-commit: 4c3a0dd56b4ef99ac8c57cfde61f792088b0ff4d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# REST API クックブック（クライアント/サーバー間） {#rest-api-cookbook-client-to-server}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。


## 概要 {#overview}

このドキュメントでは、プログラマーのエンジニアリングチームが「スマートデバイス」（ゲームコンソール、スマート TV アプリ、セットトップボックスなど）を REST API サービスを使用したAdobe Primetime認証の使用 このクライアント間アプローチは、クライアント SDK ではなく REST API を使用し、多数の一意の SDK の開発が実行不可能な様々なプラットフォームに対する幅広いサポートを可能にします。 クライアントレスソリューションの動作に関する幅広い技術概要については、 [クライアントレスの技術概要](/help/authentication/rest-api-overview.md).


この方法では、必要なフローを完了するには、起動、登録、承認、ビューメディアフロー（ストリーミングアプリと AuthN アプリ）の 2 つのコンポーネント（ストリーミングアプリと AuthN アプリ）が必要です。

## コンポーネント {#components}

動作中のクライアント/サーバー間ソリューションでは、次のコンポーネントが関係します。

 

| タイプ | コンポーネント | 説明 |
| --- | --- | --- |
| ストリーミングデバイス | ストリーミングアプリ | ユーザーのストリーミングデバイス上に存在し、認証済みビデオを再生するプログラマーアプリケーション。 |
|  | \[ オプション\] AuthN モジュール | ストリーミングデバイスにユーザエージェント（Web ブラウザ）がある場合、AuthN モジュールは MVPD IdP でのユーザの認証を担当します。 |
| \[ オプション\] AuthN デバイス | AuthN アプリ | ストリーミングデバイスにユーザエージェント（Web ブラウザ）がない場合、AuthN アプリケーションは、Web ブラウザを使用して別のユーザのデバイスからアクセスするプログラマの Web アプリケーションです。  |
| Adobe基盤 | Adobe Pass Service | MVPD IdP および AuthZ サービスと統合され、認証と承認の決定を提供するサービスです。 |
| MVPD Infrastructure | MVPD IdP | ユーザーの ID を検証するために、資格情報ベースの認証サービスを提供する MVPD エンドポイントです。 |
|  | MVPD AuthZ サービス | ユーザーの購読、親の制限などに基づいて認証の決定を行う MVPD エンドポイント。 |

 

フローで使用される追加の用語は、 [用語集](http://tve.helpdocsonline.com/adobe-pass-glossary).

## フロー{#flows}

### 動的クライアント登録 (DCR)

Adobe Passは、DCR を使用して、プログラマーアプリケーションまたはサーバーとAdobe Passサービス間のクライアント通信を保護します。 DCR フローは、別々の、依存する、前提条件のフローで、次の場所にあります。http://tve.helpdocsonline.com/dynamic-client-registration


### ストリーミング（スマートデバイス）アプリフロー

![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/clientless_1st_screen_updated.PNG)

 

#### 起動フロー

1. アプリが起動し、初期 UI が読み込まれます。

2. デバイス ID を取得/生成します。

3. 認証呼び出しを発行して、デバイスが既に認証されているかどうかを確認します。  例： [`<SP_FQDN>/api/v1/checkauthn [device ID]`](/help/authentication/check-authentication-token.md)

4. この `checkauthn` の呼び出しが成功したら、手順 2 以降の認証フローに進みます。  失敗した場合は、登録フローを開始します。

 

#### 登録フロー

1. ユーザーが第 2 の画面ログインアプリにアクセスする際に使用する登録コードおよび URL を取得し、ユーザーに提示します。

   a.POSTリクエストをAdobe登録コードサービスに送信し、ハッシュ化されたデバイス ID と「登録 URL」を渡します。  例： [`<REGGIE_FQDN>/reggie/v1/[requestorId]/regcode [device ID]`](/help/authentication/registration-code-request.md)

   b.返された登録コードと URL をユーザーに提示します。

   c. Web 対応デバイスに切り替えるようにユーザーに指示し、URL に移動して、登録コードを入力します。

 

#### 認証フロー

1. ユーザーは 2 つ目のスクリーンアプリから戻り、デバイスの「続行」ボタンを押します。 または、ポーリングメカニズムを実装して認証状態を確認することもできますが、Adobe Primetime認証では、ポーリングの実行時に「続行」ボタンを使用する方法を推奨しています。 <!--(For information on employing a "Continue" button versus polling the Adobe Primetime authentication backend server, see the Clientless Technical Overview: Managing 2nd-Screen Workflow Transition.)--> 例： [\&lt;sp _fqdn=&quot;&quot;>/api/v1/tokens/authn](/help/authentication/retrieve-authentication-token.md)

2. 認証を開始するGETリクエストをAdobe Primetime認証認証サービスに送信します。 例： `<SP_FQDN>/api/v1/authorize [device ID, Requestor ID, Resource ID]`

<!-- end list -->

- 応答が成功を示す場合：ユーザーに有効な AuthN トークンがあり、ユーザーはリクエストされたメディアを視聴する権限があります（このユーザーには有効な AuthZ トークンがあります）。

- 応答が失敗を示す場合：例外のタイプ（AuthN、AuthZ、またはその他）を確認するために、次の例外がスローされます。

   - AuthN エラーの場合は、登録フローを再起動します。

   - AuthZ エラーの場合は、要求されたメディアを視聴する権限がユーザーになく、何らかのエラーメッセージがユーザーに表示されます。

   - その他のエラー（接続エラー、ネットワークエラーなど）が 次に、適切なエラーメッセージをユーザーに表示します。

 

#### メディアフローの表示

1. メディアの選択肢を提示します。 ユーザは、表示するメディアを選択する。

2. メディアは保護されていますか？

   a.アプリは、メディアが保護されているかどうかを確認します。

   b.メディアが保護されている場合、アプリは上記の認証 (AuthZ) フローを開始します。

   c.メディアが保護されていない場合は、ユーザーのメディアを再生します。

3. メディアを再生します。


### AuthN（2 番目の画面）アプリフロー

![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/smart_dev_second_flow.png)

1. このユーザーの MVPD のリストを取得します。 例： [`<SP_FQDN>/api/v1/config/[requestorID]`](/help/authentication/provide-mvpd-list.md)

1. 認証フローを開始します。  例： [`<SP_FQDN>/api/v1/authenticate [requestorID, MVPD ID, Redirect URL, Domain name, Registration Code, "noflash=true"]`](/help/authentication/initiate-authentication.md)

1. 認証が成功したかどうかを確認します。  例： [`<SP_FQDN>/api/v1/checkauthn/[registration code][requestor ID]`](/help/authentication/check-authentication-token.md)

1. ユーザーをスマートデバイスアプリに送り返し、認証フローを完了します。

 

## Platform SSO {#platform-sso}

一部のプラットフォームでは、シングルサインオン (SSO) を専用でサポートしています。 実装の詳細は、各プラットフォームで確認できます。

- [Apple SSO](http://tve.helpdocsonline.com/rest-api-apple-sso)
- Amazon SSO

## REST API 用の TempPass とプロモーション用の TempPass {#temppass}

ユーザーが資格情報を入力する必要がない TempPass およびプロモーション TempPass 実装の場合、認証をストリーミングアプリで直接実装できます。 

**この API を使用するには、ストリーミングアプリで、デバイス ID が、オプションの追加データと共にトークンを識別するために使用されるので、一意性を確認する必要があります。**


![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/Free%20preview%20option.png?dc=201612071020-0)

### 関連情報 {#related}

- [REST API リファレンス](/help/authentication/rest-api-reference.md)
