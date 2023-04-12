---
title: Amazon FireOS 統合クックブック
description: Amazon FireOS 統合クックブック
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1433'
ht-degree: 0%

---


# Amazon FireOS 統合クックブック {#amazon-fireos-integration-cookbook}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

</br>


## はじめに {#intro}

このドキュメントでは、Amazon FireOS AccessEnabler ライブラリによって公開される API を使用して、プログラマーの上位レベルアプリケーションが実装できる使用権限ワークフローについて説明します。

Amazon FireOS のAdobe Primetime認証権限付与ソリューションは、最終的に次の 2 つのドメインに分割されます。

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

AccessEnabler のネットワーク・アクティビティは別のスレッドで実行されるため、UI スレッドはブロックされません。 その結果、2 つのアプリケーションドメイン間の双方向通信チャネルは、完全に非同期のパターンに従う必要があります。

- UI アプリケーション・レイヤは、AccessEnabler ライブラリによって公開された API 呼び出しを介して、AccessEnabler ドメインにメッセージを送信します。
- AccessEnabler は、UI 層が AccessEnabler ライブラリに登録する AccessEnabler プロトコルに含まれるコールバックメソッドを使用して、UI 層に応答します。

## 権利付与フロー {#entitlement}

1. [前提条件](#prereqs)
1. [起動フロー](#startup_flow)
1. [認証フロー](#authn_flow)
1. [認証フロー](#authz_flow)
1. [メディアフローの表示](#media_flow)
1. [ログアウトフロー](#logout_flow)

 

### A.前提条件 {#prereqs}

1. コールバック関数を作成します。
   - [&#39;setRequestorComplete()&#39;](#$setRequestorComplete)

      - トリガー者 `setRequestor()`の場合は、成功または失敗を返します。     成功の場合は、使用権限の呼び出しを続行できます。
   - [displayProviderDialog(mvpds)](#$displayProviderDialog)

      - トリガー者 `getAuthentication()` ユーザーがプロバイダー (MVPD) を選択せず、まだ認証されていない場合にのみ有効です。 この `mvpds` パラメーターは、ユーザーが使用できるプロバイダーの配列です。
   - [&#39;setAuthenticationStatus(status, reason)&#39;](#$setAuthNStatus)

      - トリガー者 `checkAuthentication()` 毎回 トリガー者 `getAuthentication()` は、ユーザーが既に認証済みで、プロバイダーを選択している場合にのみ有効です。

      - 返されるステータスは認証済みまたは未認証です。理由は、認証の失敗またはログアウトアクションを示しています。
   - [navigateToUrl(url)](#$navigateToUrl)

      - AmazonFireOS SDK では無視され、メソッドは、がトリガーされる Android プラットフォームで使用されます。 `getAuthentication()` ユーザが MVPD を選択した後。  この `url` パラメータは、MVPD のログインページの場所を提供します。
   - [&#39;sendTrackingData(event, data)&#39;](#$sendTrackingData)

      - トリガー者 `checkAuthentication(), getAuthentication(), checkAuthorization(), getAuthorization(), setSelectedProvider()`.
この `event` パラメーターは発生したエンタイトルメントイベントを示し、 `data` パラメーターは、イベントに関連する値のリストです。 
   - [&#39;setToken(token, resource)&#39;](#$setToken)

      - トリガー者 `checkAuthorization()` および `getAuthorization()` リソースを表示するための認証が成功した後。
      - この `token` パラメーターは短時間のみ有効なメディアトークンで、 `resource` パラメーターは、ユーザーが表示を許可されるコンテンツです。
   - [&#39;tokenRequestFailed(resource, code, description)&#39;](#$tokenRequestFailed)

      - トリガー者 `checkAuthorization()` および `getAuthorization()` 認証に失敗した後。
      - この `resource` パラメーターは、ユーザーが表示しようとしたコンテンツです。の `code` パラメータは、発生したエラーの種類を示すエラーコードです。の `description` パラメーターは、エラーコードに関連するエラーを示します。
   - [&#39;selectedProvider(mvpd)&#39;](#$selectedProvider)

      - トリガー者 `getSelectedProvider()`.
      - この `mvpd` パラメーターは、ユーザーが選択したプロバイダーに関する情報を提供します。
   - [&#39;setMetadataStatus(metadata, key, arguments)&#39;](#$setMetadataStatus)

      - トリガー者 `getMetadata().`
      - この `metadata` パラメーターは、要求した特定のデータを提供します。の `key` パラメーターは、 `getMetadata()` 要求そして `arguments` パラメーターは、に渡された辞書と同じです。 `getMetadata()`.
   - [&#39;preauthorizedResources(resources)&#39;](#$preauthResources)

      - トリガー者 `checkPreauthorizedResources()`.
      - この `authorizedResources` パラメーターは、ユーザーが表示する権限を持つリソースを表示します。\
          










![](assets/android-entitlement-flows.png)\
 

### B.起動フロー {#startup_flow}

1. 上位レベルのアプリケーションを起動します。
1. Adobe Primetime認証の開始
   1. 呼び出し [`getInstance`](#$getInstance) : Adobe Primetime認証 AccessEnabler の 1 つのインスタンスを作成します。

      - **依存関係：** Adobe Primetime認証ネイティブAmazon FireOS ライブラリ (AccessEnabler)
   2. 呼び出し` setRequestor()` プログラマの識別子を確立するプログラマーズに入る `requestorID` と（オプション） Adobe Primetime認証エンドポイントの配列。

      - **依存関係：** 有効なAdobe Primetime認証 RequestorID (Adobe Primetime認証アカウントマネージャーにお問い合わせのうえ、お手数です )

      - **トリガー:** setRequestorComplete() コールバック

   要求者 ID が完全に確立されるまで、エンタイトルメントリクエストを完了できません。 つまり、setRequestor() が実行中でも、以降のすべてのエンタイトルメントリクエスト (`checkAuthentication()`) がブロックされました。

   次の 2 つの実装オプションがあります。要求者の識別情報がバックエンドサーバに送信されると、UI アプリケーションレイヤーは次の 2 つの方法のいずれかを選択できます。</p>

   1. トリガーされるまで待つ `setRequestorComplete()` コールバック（AccessEnabler デリゲートの一部）  このオプションは、 `setRequestor()` 完了したので、ほとんどの実装で推奨されます。

   1. トリガーされるのを待たずに続行 `setRequestorComplete()` コールバックを実行し、エンタイトルメントリクエストの発行を開始します。 これらの呼び出し (checkAuthentication、checkAuthorization、getAuthorization、getAuthorization、checkPreauthorizedResource、getMetadata、logout) は、AccessEnabler ライブラリによってキューに登録され、 `setRequestor()`. 例えば、ネットワーク接続が不安定な場合などに、このオプションが中断される場合があります。




1. 呼び出し [checkAuthentication()](#$checkAuthN) をクリックして、認証フロー全体を開始せずに、既存の認証を確認します。  この呼び出しが成功した場合は、認証フローに直接進むことができます。  そうでない場合は、認証フローに進みます。

- **依存関係：** への呼び出しが成功しました `setRequestor()` （この依存関係は、後続のすべての呼び出しにも適用されます）。

- **トリガー:** setAuthenticationStatus() コールバック

### ハ。認証フロー {#authn_flow}

1. 呼び出し [`getAuthentication()`](#$getAuthN) 認証フローを開始するか、ユーザーが既に認証済みであることを確認する場合。 

   **トリガー:**  

   - ユーザーが既に認証されている場合は、 setAuthenticationStatus() コールバック。  この場合は、に直接進みます。 [認証フロー](#authz_flow).
   - ユーザーがまだ認証されていない場合は、 displayProviderDialog() コールバック。  

1. に送信されるプロバイダーのリストをユーザーに提示する `displayProviderDialog()`.

1. ユーザーがプロバイダを選択すると、WebView がプロバイダページを開き、ユーザーがログインできるようにします

   **注意：** この時点で、ユーザーは認証フローをキャンセルできます。 この場合、AccessEnabler は内部状態をクリーンアップし、認証フローをリセットします。

1. ユーザーが正常にログインすると、WebView が閉じます。

1. 呼び出し `getAuthenticationToken(),` これは、AccessEnabler に対して、バックエンド・サーバから認証トークンを取得するよう指示します。 

1. [オプション] 呼び出し [`checkPreauthorizedResources(resources)`](#$checkPreauth) をクリックして、ユーザーが表示する権限を持つリソースを確認します。 この `resources` パラメーターは、ユーザーの認証トークンに関連付けられている保護されたリソースの配列です。\
   **トリガー:** `preAuthorizedResources()` callback\
   **実行ポイント：** 認証フローの完了後

1. 認証に成功した場合は、認証フローに進みます。

 

### ニ。承認フロー {#authz_flow}

1. 呼び出し [`getAuthorization()`](#$getAuthZ) をクリックして認証フローを開始します。

   依存関係：有効な ResourceID が MVPD に合意されました。

   **注意：** ResourceID は、他のデバイスやプラットフォームで使用されるものと同じである必要があり、MVPD 間で同じである必要があります。

1. 認証と承認を検証します。

   - この `getAuthorization()` 呼び出しが成功しました。ユーザーには有効な AuthN および AuthZ トークンがあります（ユーザーは認証され、リクエストされたメディアを視聴する権限を持っています）。
   - If `getAuthorization()` 失敗：例外のタイプ（AuthN、AuthZ、またはその他）を確認するために、次の例外がスローされます。
      - 認証 (AuthN) エラーの場合は、認証フローを再起動します。
      - 認証 (AuthZ) エラーの場合、ユーザーはリクエストされたメディアを視聴する権限がなく、何らかのエラーメッセージがユーザーに表示されます。
      - その他のタイプのエラー（接続エラー、ネットワークエラーなど）が 次に、適切なエラーメッセージをユーザーに表示します。

1. ショートメディアトークンを検証します。

   Adobe Primetime認証メディアトークン検証ライブラリを使用して、 `getAuthorization()` 上記の呼び出し：

   - 検証が成功した場合：ユーザーに必要なメディアを再生します。
   - 検証が失敗した場合：AuthZ トークンが無効で、メディアリクエストが拒否され、エラーメッセージがユーザーに表示される必要があります。

1. 通常のアプリケーションフローに戻ります。

### E.メディアフローの表示 {#media_flow}

1. ユーザーが表示するメディアを選択します。
1.  メディアは保護されていますか？  選択したメディアが保護されているかどうかをアプリケーションが確認します。
   - 選択したメディアが保護されている場合、アプリケーションは [認証フロー](#authz_flow) 上
   - 選択したメディアが保護されていない場合は、ユーザーのメディアを再生します。

### F.ログアウトフロー {#logout_flow}

1. 呼び出し [`logout()`](#$logout) をクリックして、ユーザーをログアウトします。 \
   AccessEnabler は、シングルサインオンを通じてログインを共有するすべてのリクエスタに対して、現在の MVPD に対してユーザーが取得した、キャッシュされた値とトークンをすべて消去します。 キャッシュをクリアした後、AccessEnabler は、サーバ側セッションをクリーンアップするためのサーバ呼び出しを行います。  サーバー呼び出しによって IdP に SAML リダイレクトが発生する可能性があるので（IdP 側でのセッションのクリーンアップが可能）、この呼び出しはすべてのリダイレクトに従う必要があります。 このため、この呼び出しは WebView コントロール内で処理されます（ユーザーには表示されません）。

   **注意：** ログアウトフローは、ユーザーが WebView と何らかのやり取りをする必要がないという点で、認証フローとは異なります。 したがって、WebView コントロールを非表示にする（次のようにする）ことが可能です。非表示 ) をログアウトプロセス中に使用します。

