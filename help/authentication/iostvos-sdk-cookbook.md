---
title: iOS/tvOS クックブック
description: iOS/tvOS クックブック
source-git-commit: 49d5d8c1de263bd63db642d71a5bbb926fa45f96
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# iOS/tvOS SDK クックブック {#iostvos-sdk-cookbook}

- [はじめに](#intro)
- [権利付与フロー](#entitlement)
- [関連情報](#related)

>[!NOTE]
>
>**通知**:このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

</br>


## はじめに {#intro}

このドキュメントでは、iOS/tvOS AccessEnabler ライブラリによって公開された API を使用して、プログラマーの上位レベルアプリケーションが実装できる使用権限ワークフローについて説明します。

 

iOS/tvOS のAdobe Primetime認証権限付与ソリューションは、最終的に次の 2 つのドメインに分割されます。

- UI ドメイン — UI を実装し、AccessEnabler ライブラリが提供するサービスを使用して、制限されたコンテンツへのアクセスを提供する上位レベルのアプリケーション層です。
- AccessEnabler ドメイン — エンタイトルメントワークフローは、次の形式で実装されます。
   - Adobeのバックエンドサーバーに対しておこなわれたネットワーク呼び出し
   - 認証ワークフローと承認ワークフローに関連するビジネスロジックルール
   - 様々なリソースの管理とワークフロー状態の処理（トークンキャッシュなど）

AccessEnabler ドメインの目的は、権限付与ワークフローの複雑さをすべて非表示にし、権限付与ワークフローを実装するシンプルな権限付与プリミティブのセットを（AccessEnabler ライブラリを通じて）上層のアプリケーションに提供することです。

1. 要求者 ID を設定
1. 特定の ID プロバイダーに対する認証の確認と取得
1. 特定のリソースの認証を確認し、取得する
1. ログアウト
1. Apple VSA フレームワークをプロキシすることによるApple SSO フロー

AccessEnabler のネットワーク・アクティビティは、AccessEnabler のスレッドで実行されるため、UI スレッドはブロックされません。 その結果、2 つのアプリケーションドメイン間の双方向通信チャネルは、完全に非同期のパターンに従う必要があります。

- UI アプリケーション・レイヤは、AccessEnabler ライブラリによって公開された API 呼び出しを介して、AccessEnabler ドメインにメッセージを送信します。
- AccessEnabler は、UI 層が AccessEnabler ライブラリに登録する AccessEnabler プロトコルに含まれるコールバックメソッドを使用して、UI 層に応答します。

 

## 訪問者 ID の設定 {#visitorIDSetup}

の設定 [Marketing CloudvisitorID](https://marketing.adobe.com/resources/help/en_US/mcvid/) の値は、分析の観点から非常に重要です。 visitorID 値を設定すると、SDK はこの情報をネットワーク呼び出しごとに送信し、Adobe Primetime Authentication サーバーはこの情報を収集します。 今後、Adobe Primetime認証サービスの分析を、他のアプリケーションや Web サイトから取得した他の分析レポートと関連付けることができます。 visitorID の設定方法に関する情報は、を参照してください。 [ここ](#setOptions).

 

## 権利付与フロー {#entitlement}

A.  [前提条件](#prereqs) </br>
B.  [起動フロー](#startup_flow) </br>
C.  [Apple SSO を使用しない認証フロー](#authn_flow_wo_applesso)  </br>
D.  [iOSでのApple SSO での認証フロー](#authn_flow_with_applesso) </br>
E.  [tvOS でのApple SSO での認証フロー](#authn_flow_with_applesso_tvOS) </br>
金。  [認証フロー](#authz_flow) </br>
G.  [メディアフローの表示](#media_flow) </br>
H.  [Apple SSO を使用しないログアウトフロー](#logout_flow_wo_AppleSSO) </br>
I.  [Apple SSO でのログアウトフロー](#logout_flow_with_AppleSSO) </br>

 

### A.前提条件 {#prereqs}

1. コールバック関数を作成します。
   - `setRequestorComplete()` </br>
      - トリガー者 [setRequestor()](#$setReq)の場合は、成功または失敗を返します。 </br>
      - 成功の場合は、使用権限の呼び出しを続行できます。
   - [`displayProviderDialog(mvpds)`](#$dispProvDialog) </br>
      - トリガー者 [`getAuthentication()`](#$getAuthN) ユーザーがプロバイダー (MVPD) を選択せず、まだ認証されていない場合にのみ有効です。 </br>
      - この `mvpds` パラメーターは、ユーザーが使用できるプロバイダーの配列です。
   - `setAuthenticationStatus(status, errorcode)` </br>
      - トリガー者 `checkAuthentication()` 毎回  </br>
      - トリガー者 [`getAuthentication()`](#$getAuthN) は、ユーザーが既に認証済みで、プロバイダーを選択している場合にのみ有効です。 </br>
      - 返されるステータスは成功または失敗です。エラーコードは、失敗のタイプを示します。
   - [`navigateToUrl(url)`](#$nav2url) </br>
      - トリガー者 [`getAuthentication()`](#$getAuthN) ユーザが MVPD を選択した後。  この `url` パラメータは、MVPD のログインページの場所を提供します。
   - `sendTrackingData(event, data)` </br>
      - トリガー者 `checkAuthentication()`, [`getAuthentication()`](#$getAuthN), `checkAuthorization()`, [`getAuthorization()`](#$getAuthZ), `setSelectedProvider()`.
      - この `event` パラメーターは、発生したエンタイトルメントイベントを示します。の `data` パラメーターは、イベントに関連する値のリストです。 
   - `setToken(token, resource)`

      - トリガー者 [checkAuthorization()](#checkAuthZ) および [getAuthorization()](#$getAuthZ) リソースを表示するための認証が成功した後。
      - この `token` パラメーターは短時間のみ有効なメディアトークンです。の `resource` パラメーターは、ユーザーが表示を許可されるコンテンツです。
   - `tokenRequestFailed(resource, code, description)` </br>
      - トリガー者 [checkAuthorization()](#checkAuthZ) および [getAuthorization()](#$getAuthZ) 認証に失敗した後。
      - この `resource` パラメーターは、ユーザーが表示しようとしたコンテンツです。の `code` パラメータは、発生したエラーの種類を示すエラーコードです。の `description` パラメーターは、エラーコードに関連するエラーを示します。
   - `selectedProvider(mvpd)` </br>
      - トリガー者 [`getSelectedProvider()`](#getSelProv).
      - この `mvpd` パラメーターは、ユーザーが選択したプロバイダーに関する情報を提供します。
   - `setMetadataStatus(metadata, key, arguments)`
      - トリガー者 `getMetadata().`
      - この `metadata` パラメーターは、要求した特定のデータを提供します。の
         `key` パラメーターは、 [getMetadata()](#getMeta)
要求そして 
`arguments` パラメーターは、に渡された辞書と同じです。 [getMetadata()](#getMeta).
   - [&#39;preauthorizedResources(authorizedResources)&#39;](#preauthResources)

      - トリガー者 [`checkPreauthorizedResources()`](#checkPreauth).
      - この `authorizedResources` パラメーターは、ユーザーが表示する権限を持つリソースを表示します。
   - [&#39;presentTvProviderDialog(viewController)&#39;](#presentTvDialog)
      - トリガー者 [getAuthentication()](#getAuthN) 現在のリクエスト元が、少なくとも SSO サポートを持つ MVPD をサポートしている場合。
      - viewController パラメーターはApple SSO ダイアログで、メインビューコントローラーに表示する必要があります。
   - [&#39;dismissTvProviderDialog(viewController)&#39;](#dismissTvDialog)
      - (Apple SSO ダイアログから「キャンセル」または「その他の TV プロバイダー」を選択する ) ユーザーアクションによってトリガーされます。
      - viewController パラメーターはApple SSO ダイアログで、メインビューコントローラーから閉じる必要があります。












</br>


![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/iOS_flows\(1\).png)\
 

### B.起動フロー {#startup_flow}

1. 上位レベルのアプリケーションを起動します。</br>
1. Adobe Primetime認証の開始 </br></br>
a.呼び出し [`init`](#$init) : Adobe Primetime認証 AccessEnabler の 1 つのインスタンスを作成します。
   - **依存関係：** Adobe Primetime認証ネイティブiOS/tvOS ライブラリ (AccessEnabler)
   b.呼び出し `setRequestor()` プログラマのアイデンティティを確立するプログラマーズに入る `requestorID` および（オプション） Adobe Primetime認証エンドポイントの配列。 tvOS の場合は、公開鍵と秘密鍵も指定する必要があります。 詳しくは、 [クライアントレスドキュメント](#create_dev) 」を参照してください。
   - **依存関係：** 有効なAdobe Primetime認証 RequestorID\
      ( これを調整するには、Adobe Primetimeの認証アカウントマネージャーにお問い合わせください )。
   - **トリガー:**

      [setRequestorComplete()](#$setReqComplete) callback
   >[!NOTE]
   >
   > **注意：** 要求者 ID が完全に確立されるまで、エンタイトルメントリクエストを完了できません。 これは、実際には [`setRequestor()`](#$setReq)  が実行中の場合は、以降のすべての権限付与リクエスト ( 例： [`checkAuthentication()`](#checkAuthN) はブロックされています。

   次の 2 つの実装オプションがあります。要求者の識別情報がバックエンドサーバに送信されると、UI アプリケーションレイヤーは次の 2 つの方法のいずれかを選択できます。 </br>
   1. トリガーされるまで待つ [`setRequestorComplete()`](#setReqComplete) コールバック（AccessEnabler デリゲートの一部）  このオプションは、 [`setRequestor()`](#$setReq) 完了したので、ほとんどの実装で推奨されます。
   1. トリガーされるのを待たずに続行 [`setRequestorComplete()`](#setReqComplete) コールバックを実行し、エンタイトルメントリクエストの発行を開始します。 これらの呼び出し (checkAuthentication、checkAuthorization、getAuthorization、getAuthorization、checkPreauthorizedResource、getMetadata、logout) は、AccessEnabler ライブラリによってキューに登録され、 [`setRequestor()`](#$setReq). 例えば、ネットワーク接続が不安定な場合などに、このオプションが中断される場合があります。



1. 呼び出し `checkAuthentication()` をクリックして、認証フロー全体を開始せずに、既存の認証を確認します。  この呼び出しが成功した場合は、認証フローに直接進むことができます。  そうでない場合は、認証フローに進みます。

   - **依存関係：** への呼び出しが成功しました [setRequestor()](#$setReq)
（この依存関係は、後続のすべての呼び出しにも適用されます）。

   - **トリガー:** [setAuthenticationStatus()](#$setAuthNStatus) callback

 

### C. Apple SSO を使用しない認証フロー {#authn_flow_wo_applesso}

1. 呼び出し [`getAuthentication()`](#$getAuthN) 認証フローを開始するか、ユーザーが既に認証済みであることを確認する場合。 \
   **トリガー:**  

   - この [setAuthenticationStatus()](#$setAuthNStatus) callback：ユーザーが既に認証されている場合に使用します。  この場合は、に直接進みます。 [認証フロー](#authz_flow).
   - この [displayProviderDialog()](#$dispProvDialog) callback：ユーザーがまだ認証されていない場合に使用します。  

1. に送信されるプロバイダーのリストをユーザーに提示する
   [`displayProviderDialog()`](#dispProvDialog).

1. ユーザーがプロバイダーを選択した後、 `navigateToUrl:` または `navigateToUrl:useSVC:` コールバックを呼び出し、を開きます。 `UIWebView/WKWebView` または `SFSafariViewController` コントローラーに接続し、そのコントローラーを URL に転送します。   

1. を通じて `UIWebView/WKWebView` または `SFSafariViewController` 前の手順でインスタンス化されたので、ユーザーは MVPD のログインページに移動し、ログイン資格情報を入力します。 コントローラ内では、いくつかのリダイレクト操作が行われます。</br></br>
   **注意**  — この時点で、ユーザーは認証フローをキャンセルできます。 この場合、UI レイヤは、 [setSelectedProvider()](#setSelProv) と `null` をパラメーターとして使用します。 これにより、AccessEnabler は内部状態をクリーンアップし、認証フローをリセットできます。

1. ユーザーが正常にログインすると、アプリケーションレイヤーは、特定のカスタム URL の読み込みを検出します。 この特定のカスタム URL は実際には無効で、コントローラが実際に読み込むことを意図していないことに注意してください。 アプリケーションで、認証フローが完了し、安全に `UIWebView/WKWebView` または `SFSafariViewController` コントローラ。 例： `SFSafariViewController `コントローラーは、 **`application's custom scheme`** ( 例：`adbe.u-XFXJeTSDuJiIQs0HVRAg://adobe.com`) が含まれていない場合、この特定のカスタム URL は **`ADOBEPASS_REDIRECT_URL`** 定数 ( `adobepass://ios.app`) をクリックします。

1. UIWebView/WKWebView または SFSafariViewController コントローラを閉じ、AccessEnabler の `handleExternalURL:url `API メソッド`,` これは、AccessEnabler に対して、バックエンド・サーバから認証トークンを取得するよう指示します。 

1. [オプション] 呼び出し    [`checkPreauthorizedResources(resources)`](#$checkPreauth) をクリックして、ユーザーが表示する権限を持つリソースを確認します。  この `resources` パラメーターは、ユーザーの認証トークンに関連付けられている保護されたリソースの配列です。  ユーザーの MVPD から取得した認証情報の 1 つの用途は、UI を飾ることです（例えば、保護されたコンテンツの横にロック/ロック解除されたシンボル）。

   - **トリガー:** [`preauthorizedResources()`](#preauthResources) callback
   - **実行ポイント：** 認証フローの完了後

1. 認証に成功した場合は、認証フローに進みます。

 

### D. iOSでのApple SSO での認証フロー {#authn_flow_with_applesso}

1. 呼び出し [`getAuthentication()`](#$getAuthN) 認証フローを開始するか、ユーザーが既に認証済みであることを確認する場合。 \
   **トリガー:**  

   - この [presentTvProviderDialog()](#presentTvDialog) ユーザーが認証されておらず、現在の要求元が少なくとも SSO をサポートする MVPD を持っている場合は、callback 。 MVPD が SSO をサポートしない場合は、従来の認証フローが使用されます。

1. ユーザーがプロバイダを選択すると、AccessEnabler ライブラリは、Appleの VSA フレームワークで提供された情報を使用して認証トークンを取得します。

1. この [setAuthenticationsStatus()](#setAuthNStatus) コールバックがトリガーされます。 この時点で、ユーザーはApple SSO で認証されます。

1. [オプション] 呼び出し [`checkPreauthorizedResources(resources)`](#$checkPreauth) をクリックして、ユーザーが表示する権限を持つリソースを確認します。 この `resources` パラメーターは、ユーザーの認証トークンに関連付けられている保護されたリソースの配列です。  ユーザーの MVPD から取得した認証情報の 1 つの用途は、UI を飾ることです（例えば、保護されたコンテンツの横にロック/ロック解除されたシンボル）。

   - **トリガー:** [`preauthorizedResources()`](#preauthResources) callback
   - **実行ポイント：** 認証フローの完了後

1. 認証に成功した場合は、認証フローに進みます。

 

### E. tvOS でのApple SSO での認証フロー {#authn_flow_with_applesso_tvOS}

1. 呼び出し [`getAuthentication()`](#$getAuthN) 認証フローを開始するか、ユーザーが既に認証済みであることを確認する場合。 \
   **トリガー:**  
   - この [`presentTvProviderDialog()`](#presentTvDialog) ユーザーが認証されておらず、現在の要求元が少なくとも SSO をサポートする MVPD を持っている場合は、callback 。 MVPD が SSO をサポートしない場合は、従来の認証フローが使用されます。

1. ユーザーがプロバイダーを選択した後、 [`status()`](#status_callback_implementation) コールバックが呼び出されます。 登録コードが提供され、AccessEnabler ライブラリが、正常な 2 番目の画面認証を行うためにサーバのポーリングを開始します。

1. 指定した登録コードが 2 番目の画面で正常に認証するために使用されている場合、 [`setAuthenticatiosStatus()`](#setAuthNStatus) コールバックがトリガーされます。 この時点で、ユーザーはApple SSO で認証されます。
1. [オプション] 呼び出し [`checkPreauthorizedResources(resources)`](#$checkPreauth) をクリックして、ユーザーが表示する権限を持つリソースを確認します。 この `resources` パラメーターは、ユーザーの認証トークンに関連付けられている保護されたリソースの配列です。  ユーザーの MVPD から取得した認証情報の 1 つの用途は、UI を飾ることです（例えば、保護されたコンテンツの横にロック/ロック解除されたシンボル）。
   - **トリガー:** [`preauthorizedResources()`](#preauthResources) callback
   - **実行ポイント：** 認証フローの完了後
1. 認証に成功した場合は、認証フローに進みます。

 

### ヘ。承認フロー {#authz_flow}

1. 呼び出し [getAuthorization()](#$getAuthZ) をクリックして認証フローを開始します。
   - **依存関係：** 有効な ResourceID が MVPD に合意されました。
   - リソース ID は、他のデバイスやプラットフォームで使用される ID と同じである必要があり、MVPD 間で同じになります。 リソース ID について詳しくは、 [保護されたリソースの識別](https://tve.helpdocsonline.com/4-2-2-3)

1. 認証と承認を検証します。

   - この [getAuthorization()](#$getAuthZ) 呼び出しが成功しました。ユーザーには有効な AuthN および AuthZ トークンがあります（ユーザーは認証され、リクエストされたメディアを視聴する権限を持っています）。
   - If [getAuthorization()](#$getAuthZ) 失敗：例外のタイプ（AuthN、AuthZ、またはその他）を確認するために、次の例外がスローされます。
      - 認証 (AuthN) エラーの場合は、認証フローを再起動します。
      - 認証 (AuthZ) エラーの場合、ユーザーはリクエストされたメディアを視聴する権限がなく、何らかのエラーメッセージがユーザーに表示されます。
      - その他のタイプのエラー（接続エラー、ネットワークエラーなど）が 次に、適切なエラーメッセージをユーザーに表示します。

1. ショートメディアトークンを検証します。\
   Adobe Primetime認証メディアトークン検証ライブラリを使用して、 [getAuthorization()](#$getAuthZ) 上記の呼び出し：

   - 検証が成功した場合：ユーザーに必要なメディアを再生します。
   - 検証が失敗した場合：AuthZ トークンが無効で、メディアリクエストが拒否され、エラーメッセージがユーザーに表示される必要があります。


1. 通常のアプリケーションフローに戻ります。

 

### G.メディアフローの表示 {#media_flow}

1. ユーザーが表示するメディアを選択します。
1. メディアは保護されていますか？  選択したメディアが保護されているかどうかをアプリケーションが確認します。
   - 選択したメディアが保護されている場合、アプリケーションは [認証フロー](#authz_flow) 上
   - 選択したメディアが保護されていない場合は、ユーザーのメディアを再生します。

 

### H.ログアウトフロー (Apple SSO なし ) {#logout_flow_wo_AppleSSO}

1. 呼び出し [`logout()`](#$logout) をクリックして、ユーザーをログアウトします。 AccessEnabler は、キャッシュされた値とトークンをすべて消去します。 キャッシュをクリアした後、AccessEnabler は、サーバ側セッションをクリーンアップするためのサーバ呼び出しを行います。 サーバー呼び出しによって IdP に SAML リダイレクトが発生する可能性があるので（IdP 側でのセッションのクリーンアップが可能）、この呼び出しはすべてのリダイレクトに従う必要があります。 この理由から、この呼び出しは UIWebView/WKWebView または SFSafariViewController コントローラー内で処理する必要があります。

   - a.認証ワークフローと同じパターンに従って、AccessEnabler ドメインは、 `navigateToUrl:` または `navigateToUrl:useSVC:` コールバック。UIWebView/WKWebView または SFSafariViewController コントローラーを作成し、コールバックの `url` パラメーター。 バックエンドサーバー上のログアウトエンドポイントの URL です。

   - b.アプリケーションは、 `UIWebView/WKWebView or SFSafariViewController` コントローラーを使用し、特定のカスタム URL を読み込むタイミングを検出します。このタイミングは、複数のリダイレクトを経由します。 この特定のカスタム URL は実際には無効で、コントローラが実際に読み込むことを意図していないことに注意してください。 ログアウトフローが完了したこと、およびログアウトフローを安全に閉じられることを示すシグナルとして、アプリケーションでのみ解釈する必要があります。 `UIWebView/WKWebView` または `SFSafariViewController` コントローラ。 コントローラーがこの特定のカスタム URL を読み込むと、アプリケーションは `UIWebView/WKWebView or SFSafariViewController` コントローラと AccessEnabler の呼び出し `handleExternalURL:url`API メソッド。 例： `SFSafariViewController`コントローラーは、 **`application's custom scheme`** ( 例： `adbe.u-XFXJeTSDuJiIQs0HVRAg://adobe.com`) が含まれていない場合、この特定のカスタム URL は **`ADOBEPASS_REDIRECT_URL`**  定数 ( `adobepass://ios.app`) をクリックします。

      >[!NOTE]
      >
      > **注意：** ログアウトフローは、ユーザーが UIWebView/WKWebView や SFSafariViewController と何らかの方法でやり取りする必要がないという点で、認証フローとは異なります。 UI アプリケーションレイヤーは、すべてのリダイレクトに従っていることを確認するために、 UIWebView/WKWebView または SFSafariViewController を使用します。 したがって、ログアウトプロセス中にコントローラを非表示（非表示）にする（推奨）ことが可能です。


### I.ログアウトフロー (Apple SSO を使用 ) {#logout_flow_with_AppleSSO}

1. 呼び出し [`logout()`](#$logout) をクリックして、ユーザーをログアウトします。 
1. この [status()](#status_callback_implementation) コールバックは、id VSA203 で呼び出されます。
1. ユーザーは、システム設定からもログインするように指示される必要があります。 これに失敗すると、アプリケーションが再起動されたときに再認証がおこなわれます。

</br>

### 関連情報 {#related}

<!---
- [iOS API Reference](#)

- [iOS Technical Overview](#)

- [Generating Digital Certificates](#)

- [Identifying Protected Resources](#)

- [Handling MVPDs with 'Not Trusted Certificates' in Adobe Primetime
  authentication native SDK (Tech Note) ](#)

- [iOS Authentication error - adobepass.ios.app cannot be found (Tech
  Note)](#)
-->
