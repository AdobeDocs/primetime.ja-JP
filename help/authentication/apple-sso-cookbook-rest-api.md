---
title: Apple SSO クックブック (REST API)
description: Apple SSO クックブック (REST API)
source-git-commit: 326f97d058646795cab5d062fa5b980235f7da37
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 0%

---


# Apple SSO クックブック (REST API) {#apple-sso-cookbook-rest-api}

>[!NOTE]
>
>このページのコンテンツは、情報提供の目的でのみ提供されます。 この API を使用するには、Adobeの現在のライセンスが必要です。 不正な使用は許可されていません。

## はじめに {#Introduction}

Adobe Primetime Authentication REST API は、Apple SSO ワークフローと呼ばれる方法で、iOS、iPadOS、tvOS で実行されるクライアントアプリケーションのエンドユーザーに対する、プラットフォームのシングルサインオン (SSO) 認証をサポートできます。

このドキュメントは、既存の REST API ドキュメントの拡張機能として機能します。 [ここ](/help/authentication/rest-api-reference.md).

</br>

## クックブック {#Cookbooks}

Apple SSO のユーザーエクスペリエンスを活用するには、1 つのアプリケーションで [ビデオ購読者のアカウント](https://developer.apple.com/documentation/videosubscriberaccount) Appleが開発したフレームワークですが、Adobe Primetime Authentication REST API 通信に関しては、以下に示すヒントの順序に従う必要があります。

</br>

### 認証 {#Authentication}

- [有効なAdobe認証トークンはありますか？](#Is_there_a_valid_Adobe_authentication_token)
- [ユーザーが Platform SSO でログインしているか。](#Is_the_user_logged_in_via_Platform_SSO)
- [Adobe設定を取得](#Fetch_Adobe_configuration)
- [Adobe設定で Platform SSO ワークフローを開始](#Initiate_Platform_SSO_workflow_with_Adobe_config)
- [ユーザーログインに成功したか。](#Is_user_login_successful)
- [選択した MVPD のAdobeからプロファイルリクエストを取得](#Obtain_a_profile_request_from_Adobe_for_the_selected_MVPD)
- [Adobeリクエストを Platform SSO に転送してプロファイルを取得します](#Forward_the_Adobe_request_to_Platform_SSO_to_obtain_the_profile)
- [プラットフォーム認証トークンに対する Platform SSO プロファイルのAdobe交換](#Exchange_the_Platform_SSO_profile_for_an_Adobe_authentication_token)
- [Adobeトークンは正常に生成されましたか？](#Is_Adobe_token_generated_successfully)
- [2 番目の画面認証ワークフローの開始](#Initiate_second_screen_authentication_workflow)
- [認証フローで進む](#Proceed_with_authorization_flows)

 

![](https://dzf8vqv24eqhg.cloudfront.net/userfiles/258/326/ckfinder/images/qu/platform-sso.jpeg)

</br>

#### ステップ：&quot;有効なAdobe認証トークンはありますか？&quot; {#Is_there_a_valid_Adobe_authentication_token}

>[!TIP]
>
> **<u>ヒント：</u>** これは、 [Adobe Primetime Authentication](/help/authentication/check-authentication-token.md) サービス。

</br>

#### 手順：「ユーザーは Platform SSO を使用してログインしていますか？」 {#Is_the_user_logged_in_via_Platform_SSO}

>[!TIP]
>
> **<u>ヒント：</u>** これは、 [ビデオ購読者のアカウント](https://developer.apple.com/documentation/videosubscriberaccount) フレームワーク。

- アプリケーションが [アクセス権](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmanager/1949763-checkaccessstatus) ユーザーの購読情報を入力し、ユーザーが許可した場合にのみ続行します。
- 申し込みは、 [リクエスト](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmetadatarequest) 」を参照してください。
- アプリケーションは、 [メタデータ](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmetadata) 情報。

 

>[!TIP]
>
> **<u>ヒント：</u>** コードスニペットに従い、コメントに注意を払います。

```swift
...
let videoSubscriberAccountManager: VSAccountManager = VSAccountManager();

videoSubscriberAccountManager.checkAccessStatus(options: [VSCheckAccessOption.prompt: true]) { (accessStatus, error) -> Void in
            switch (accessStatus) {
            // The user allows the application to access subscription information.
            case VSAccountAccessStatus.granted:
                    // Construct the request for subscriber account information.
                    let vsaMetadataRequest: VSAccountMetadataRequest = VSAccountMetadataRequest();

                    // This is actually the SAML Issuer not the channel ID.
                    vsaMetadataRequest.channelIdentifier = "https://saml.sp.auth.adobe.com";
    
                    // This is the subscription account information needed at this step.
                    vsaMetadataRequest.includeAccountProviderIdentifier = true;
                    
                    // This is the subscription account information needed at this step.
                    vsaMetadataRequest.includeAuthenticationExpirationDate = true;
                    
                    // This is going to make the Video Subscriber Account framework to refrain from prompting the user with the providers picker at this step. 
                    vsaMetadataRequest.isInterruptionAllowed = false;
                    
                    // Submit the request for subscriber account information - accountProviderIdentifier.
                    videoSubscriberAccountManager.enqueue(vsaMetadataRequest) { vsaMetadata, vsaError in        
                        if (vsaMetadata != nil && vsaMetadata!.accountProviderIdentifier != nil) {
                            // The vsaMetadata!.authenticationExpirationDate will contain the expiration date for current authentication session.
                            // The vsaMetadata!.authenticationExpirationDate should be compared against current date.
                            ...
                            // The vsaMetadata!.accountProviderIdentifier will contain the provider identifier as it is known for the platform configuration.
                            // The vsaMetadata!.accountProviderIdentifier represents the platformMappingId in terms of Adobe Primetime Authentication configuration.
                            ...
                            // The application must determine the MVPD id property value based on the platformMappingId property value obtained above.
                            // The application must use the MVPD id further in its communication with Adobe Primetime Authentication services.
                            ...
                            // Continue with the "Obtain a profile request from Adobe for the selected MVPD" step.
                            ...
                            // Continue with the "Forward the Adobe request to Platform SSO to obtain the profile" step.
                            ...
                        } else {
                            // The user is not authenticated at platform level, continue with the "Fetch Adobe configuration" step.
                            ...
                        }
                    }
        
            // The user has not yet made a choice or does not allow the application to access subscription information.
            default:
                // Fallback to regular authentication workflow.
                ...
            }
}
...  
```

</br>

#### ステップ：&quot;Adobe設定を取得&quot; {#Fetch_Adobe_configuration}

>[!TIP]
>
> **<u>ヒント：</u>** これは、 [Adobe Primetime Authentication](/help/authentication/provide-mvpd-list.md) サービス。


>[!TIP]
>
> **<u>ヒント：</u>** MVPD プロパティに注意してください。 *`enablePlatformServices`*, *`boardingStatus`*, *`displayInPlatformPicker`*, *`platformMappingId`*, *`requiredMetadataFields`* コードスニペットに示されたコメントには、他の手順で特に注意を払ってください。

</br>

#### 手順「Adobe設定で Platform SSO ワークフローを開始」 {#Initiate_Platform_SSO_workflow_with_Adobe_config}

>[!TIP]
>
> **<u>ヒント：</u>** これは、 [ビデオ購読者のアカウント](https://developer.apple.com/documentation/videosubscriberaccount) フレームワーク。

- アプリケーションが [アクセス権](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmanager/1949763-checkaccessstatus) ユーザーの購読情報を入力し、ユーザーが許可した場合にのみ続行します。
- アプリケーションは、 [delegate](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmanagerdelegate) VSAccountManager の
- 申し込みは、 [リクエスト](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmetadatarequest) 」を参照してください。
- アプリケーションは、 [メタデータ](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmetadata) 情報。

 

>[!TIP]
>
> **<u>ヒント：</u>** コードスニペットに従い、コメントに注意を払います。


```swift
    ...
    let videoSubscriberAccountManager: VSAccountManager = VSAccountManager();
    
    // This must be a class implementing the VSAccountManagerDelegate protocol.
    let videoSubscriberAccountManagerDelegate: VideoSubscriberAccountManagerDelegate = VideoSubscriberAccountManagerDelegate();
    
    videoSubscriberAccountManager.delegate = videoSubscriberAccountManagerDelegate;
    
    videoSubscriberAccountManager.checkAccessStatus(options: [VSCheckAccessOption.prompt: true]) { (accessStatus, error) -> Void in
                switch (accessStatus) {
                // The user allows the application to access subscription information.
                case VSAccountAccessStatus.granted:
                        // Construct the request for subscriber account information.
                        let vsaMetadataRequest: VSAccountMetadataRequest = VSAccountMetadataRequest();
    
                        // This is actually the SAML Issuer not the channel ID.
                        vsaMetadataRequest.channelIdentifier = "https://saml.sp.auth.adobe.com";
        
                        // This is the subscription account information needed at this step.
                        vsaMetadataRequest.includeAccountProviderIdentifier = true;
                        
                        // This is the subscription account information needed at this step.
                        vsaMetadataRequest.includeAuthenticationExpirationDate = true;
                        
                        // This is going to make the Video Subscriber Account framework to prompt the user with the providers picker at this step. 
                        vsaMetadataRequest.isInterruptionAllowed = true;
                        
                        // This can be computed from the [Adobe Primetime Authentication](/help/authentication/provide-mvpd-list.md) service response in order to filter the TV providers from the Apple picker.
                        vsaMetadataRequest.supportedAccountProviderIdentifiers = supportedAccountProviderIdentifiers;
    
                        // This can be computed from the [Adobe Primetime Authentication](/help/authentication/provide-mvpd-list.md) service response in order to sort the TV providers from the Apple picker.
                        if #available(iOS 11.0, tvOS 11, *) {
                            vsaMetadataRequest.featuredAccountProviderIdentifiers = featuredAccountProviderIdentifiers;
                        }
                        
                        // Submit the request for subscriber account information - accountProviderIdentifier.
                        videoSubscriberAccountManager.enqueue(vsaMetadataRequest) { vsaMetadata, vsaError in                        
                            // This represents the checks for the "Is user login successful?" step.
                            if (vsaMetadata != nil && vsaMetadata!.accountProviderIdentifier != nil) {
                                // The vsaMetadata!.authenticationExpirationDate will contain the expiration date for current authentication session.
                                // The vsaMetadata!.authenticationExpirationDate should be compared against current date.
                                ...
                                // The vsaMetadata!.accountProviderIdentifier will contain the provider identifier as it is known for the platform configuration.
                                // The vsaMetadata!.accountProviderIdentifier represents the platformMappingId in terms of Adobe Primetime Authentication configuration.
                                ...
                                // The application must determine the MVPD id property value based on the platformMappingId property value obtained above.
                                // The application must use the MVPD id further in its communication with Adobe Primetime Authentication services.
                                ...
                                // Continue with the "Obtain a profile request from Adobe for the selected MVPD" step.
                                ...
                                // Continue with the "Forward the Adobe request to Platform SSO to obtain the profile" step.
                                ...
                            } else {
                                // The user is not authenticated at platform level.
                                if (vsaError != nil) {
                                    // The application can check to see if the user selected a provider which is present in Apple picker, but the provider is not onboarded in platform SSO.
                                    if let error: NSError = (vsaError! as NSError), error.code == 1, let appleMsoId = error.userInfo["VSErrorInfoKeyUnsupportedProviderIdentifier"] as! String? {
                                        var mvpd: Mvpd? = nil;
    
                                        // The requestor.mvpds must be computed during the "Fetch Adobe configuration" step. 
                                        for provider in requestor.mvpds {
                                            if provider.platformMappingId == appleMsoId {
                                                mvpd = provider;
                                                break;
                                            }
                                        }
                                        
                                        if mvpd != nil {
                                            // Continue with the "Initiate second screen authentcation workflow" step, but you can skip prompting the user with your MVPD picker and use the mvpd selection, therefore creating a better UX.
                                            ...
                                        } else {
                                            // Continue with the "Initiate second screen authentcation workflow" step.
                                            ...
                                        }
                                    } else {
                                        // Continue with the "Initiate second screen authentcation workflow" step.
                                        ...
                                    }
                                } else {
                                    // Continue with the "Initiate second screen authentcation workflow" step.
                                    ...
                                }
                            }
                        }
            
                // The user has not yet made a choice or does not allow the application to access subscription information.
                default:
                    // Fallback to regular authentication workflow.
                    ...
                }
    }
    ...
```

</br>

#### ステップ：「ユーザーログインに成功しましたか？」 {#Is_user_login_successful}

>[!TIP]
>
> **<u>ヒント：</u>** 次のコードスニペットに注意してください： [「Adobe設定で Platform SSO ワークフローを開始」](#Initiate_Platform_SSO_workflow_with_Adobe_config) 手順 ユーザーログインが成功した場合、 *`vsaMetadata!.accountProviderIdentifier`* に有効な値が含まれ、現在の日付が *`vsaMetadata!.authenticationExpirationDate`* の値です。

</br>

#### ステップ「選択した MVPD のAdobeからプロファイルリクエストを取得する」 {#Obtain_a_profile_request_from_Adobe_for_the_selected_MVPD}

>[!TIP]
>
> **<u>ヒント：</u>** Adobe Primetime Authentication を使用した実装 [プロファイルリクエスト](/help/authentication/retrieve-profilerequest.md) サービス。

>[!TIP]
>
> **<u>ヒント：</u>** ビデオ購読者アカウントフレームワークから取得したプロバイダー識別子は、 *`platformMappingId`* (Adobe Primetime Authentication 設定の観点から ) したがって、アプリケーションは、 *`platformMappingId`* Adobe Primetime Authentication を通じた価値 [MVPD リストを提供](/help/authentication/provide-mvpd-list.md) サービス。

</br>

#### ステップ：「Adobeリクエストを Platform SSO に転送してプロファイルを取得する」 {#Forward_the_Adobe_request_to_Platform_SSO_to_obtain_the_profile}

>[!TIP]
>
> **<u>ヒント：</u>** これは、 [ビデオ購読者のアカウント](https://developer.apple.com/documentation/videosubscriberaccount) フレームワーク。


- アプリケーションが [アクセス権](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmanager/1949763-checkaccessstatus) ユーザーの購読情報を入力し、ユーザーが許可した場合にのみ続行します。
- 申し込みは、 [リクエスト](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmetadatarequest) 」を参照してください。
- アプリケーションは、 [メタデータ](https://developer.apple.com/documentation/videosubscriberaccount/vsaccountmetadata) 情報。

 

>[!TIP]
>
> **<u>ヒント：</u>** コードスニペットに従い、コメントに注意を払います。

```swift
    ...
    let videoSubscriberAccountManager: VSAccountManager = VSAccountManager();
    
    videoSubscriberAccountManager.checkAccessStatus(options: [VSCheckAccessOption.prompt: true]) { (accessStatus, error) -> Void in
                switch (accessStatus) {
                // The user allows the application to access subscription information.
                case VSAccountAccessStatus.granted:
                        // Construct the request for subscriber account information.
                        let vsaMetadataRequest: VSAccountMetadataRequest = VSAccountMetadataRequest();
    
                        // This is actually the SAML Issuer not the channel ID.
                        vsaMetadataRequest.channelIdentifier = "https://saml.sp.auth.adobe.com";
        
                        // This is going to include subscription account information which should match the provider determined in a previous step.
                        vsaMetadataRequest.includeAccountProviderIdentifier = true;
                        
                        // This is going to include subscription account information which should match the provider determined in a previous step.
                        vsaMetadataRequest.includeAuthenticationExpirationDate = true;
                        
                        // This is going to make the Video Subscriber Account framework to refrain from prompting the user with the providers picker at this step. 
                        vsaMetadataRequest.isInterruptionAllowed = false;
    
                        // This are the user metadata fields expected to be available on a successful login and are determined from the [Adobe Primetime Authentication](/help/authentication/provide-mvpd-list.md) service. Look for the requiredMetadataFields associated with the provider determined in a previous step.
                        vsaMetadataRequest.attributeNames = requiredMetadataFields;
    
                        // This is the payload from [Adobe Primetime Authentication](/help/authentication/retrieve-profilerequest.md) service.
                        vsaMetadataRequest.verificationToken = profileRequestPayload;
                        
                        // Submit the request for subscriber account information.
                        videoSubscriberAccountManager.enqueue(vsaMetadataRequest) { vsaMetadata, vsaError in
                            if (vsaMetadata != nil && vsaMetadata!.samlAttributeQueryResponse != nil) {
                                var samlResponse: String? = vsaMetadata!.samlAttributeQueryResponse!;
                                
                                // Remove new lines, new tabs and spaces.
                                samlResponse = samlResponse?.replacingOccurrences(of: "[ \\t]+", with: " ", options: String.CompareOptions.regularExpression);
                                samlResponse = samlResponse?.components(separatedBy: CharacterSet.newlines).joined(separator: "");
                                samlResponse = samlResponse?.trimmingCharacters(in: CharacterSet.whitespacesAndNewlines);
                                
                                // Base64 encode.
                                samlResponse = samlResponse?.data(using: .utf8)?.base64EncodedString(options: []);
                                
                                // URL encode. Please be aware not to double URL encode it further.
                                samlResponse = samlResponse?.addingPercentEncoding(withAllowedCharacters: CharacterSet.init(charactersIn: "!*'();:@&=+$,/?%#[]").inverted);
                                
                                // Continue with the "Exchange the Platform SSO profile for an Adobe authentication token" step.
                                ...
                            } else {
                                // Fallback to regular authentication workflow.
                                ...
                            }
                        }
                        
                // The user has not yet made a choice or does not allow the application to access subscription information.
                default:
                    // Fallback to regular authentication workflow.
                    ...
                }
    }
    ...
```

</br>

#### ステップ：「Platform SSO プロファイルを認証トークンに交換するAdobe」 {#Exchange_the_Platform_SSO_profile_for_an_Adobe_authentication_token}

>[!TIP]
>
> **<u>ヒント：</u>** Adobe Primetime Authentication を使用した実装 [トークン交換](/help/authentication/token-exchange.md) サービス。


>[!TIP]
>
> **<u>ヒント：</u>** 次のコードスニペットに注意してください： [「Adobeリクエストを Platform SSO に転送してプロファイルを取得する」](#Forward_the_Adobe_request_to_Platform_SSO_to_obtain_the_profile) 手順 この *`vsaMetadata!.samlAttributeQueryResponse!`* は、 *`SAMLResponse`*&#x200B;を呼び出し、引き渡す必要がある [トークン交換](/help/authentication/token-exchange.md) とは、文字列の操作とエンコード (*Base64* エンコード済み *URL* エンコードされた後 ) を使用してから呼び出しをおこないます。

</br>

#### ステップ：「Adobeトークンは正常に生成されましたか？」 {#Is_Adobe_token_generated_successfully}

>[!TIP]
>
> **<u>ヒント：</u>** メディアのAdobe Primetime Authentication を使用して実装します。 [トークン交換](/help/authentication/token-exchange.md) 成功した応答 ( これは *`204 No Content`*：トークンが正常に作成され、認証フローに使用する準備が整ったことを示します。

</br>

#### ステップ：「2 番目の画面認証ワークフローの開始」 {#Initiate_second_screen_authentication_workflow}

**重要：** Apple TV では「第 2 画面認証ワークフロー」の用語が適していますが、iPhone および iPad では「第 1 画面認証ワークフロー」/「通常認証ワークフロー」の用語がより適切です。


>[!TIP]
>
> **<u>ヒント：</u>** Adobe Primetime Authentication を使用した実装

[登録コードのリクエスト](/help/authentication/registration-code-request.md), [認証の開始](/help/authentication/initiate-authentication.md) および [REST API 認証トークンの取得](/help/authentication/retrieve-authentication-token.md) または [認証トークンを確認](/help/authentication/check-authentication-token.md) サービス。


>[!TIP]
>
> **<u>ヒント：</u>** tvOS の実装については、以下の手順に従います。

- この申し込みは、 [登録コードを取得する](/help/authentication/registration-code-request.md) をクリックし、1 番目のデバイス（画面）のエンドユーザーに提示します。
- アプリケーションを起動する必要があります [認証状態を確認するポーリング](/help/authentication/retrieve-authentication-token.md) 登録コードを取得した後の第 1 の装置（画面）で。
- 別のアプリケーションが [認証を開始](/help/authentication/initiate-authentication.md) 第 2 のデバイス（画面）で登録コードが使用されている場合。
- アプリケーションを停止する必要があります [ポーリング](/help/authentication/retrieve-authentication-token.md) (1 番目のデバイス（画面）で認証トークンが生成されたとき ) に使用します。

 

>[!TIP]
>
> **<u>ヒント：</u>** iOS/iPadOS の実装については、以下の手順に従います。

- この申し込みは、 [登録コードを取得する](/help/authentication/registration-code-request.md) 1 つ目のデバイス（画面）ではエンドユーザーに提示しないでください。
- この申し込みは、 [認証を開始](/help/authentication/initiate-authentication.md) を使用して、登録コードと [WKWebView](https://developer.apple.com/documentation/webkit/wkwebview) または [SFSafariViewController](https://developer.apple.com/documentation/safariservices/sfsafariviewcontroller) コンポーネント。
- アプリケーションを起動する必要があります [認証状態を知るためのポーリング](/help/authentication/retrieve-authentication-token.md) を [WKWebView](https://developer.apple.com/documentation/webkit/wkwebview) または [SFSafariViewController](https://developer.apple.com/documentation/safariservices/sfsafariviewcontroller) コンポーネントが閉じます。
- アプリケーションを停止する必要があります [ポーリング](/help/authentication/retrieve-authentication-token.md) (1 番目のデバイス（画面）で認証トークンが生成されたとき ) に使用します。

</br>

#### ステップ：&quot;認証フローで続行&quot; {#Proceed_with_authorization_flows}

>[!TIP]
>
> **<u>ヒント：</u>** Adobe Primetime Authentication を使用した実装 [認証を開始](/help/authentication/initiate-authorization.md) および [ショートメディアトークンの取得](/help/authentication/obtain-short-media-token.md) サービス。

</br>

### ログアウト {#Logout}

この [ビデオ購読者のアカウント](https://developer.apple.com/documentation/videosubscriberaccount) framework は、デバイスのシステムレベルで TV プロバイダーアカウントにサインインしたユーザーをプログラムでログアウトする API を提供しません。 したがって、ログアウトが完全に有効になるには、エンドユーザーは次の場所から明示的にログアウトする必要があります。 *`Settings -> TV Provider`* iOS/iPadOS または *`Settings -> Accounts -> TV Provider`* tvOS の場合。 ユーザーが持つもう 1 つのオプションは、特定のアプリケーション設定セクション（TV プロバイダーのアクセス）からユーザーの購読情報にアクセスする権限を撤回することです。

>[!TIP]
>
> **<u>ヒント：</u>** Adobe Primetime Authentication を使用した実装 [ユーザーメタデータ呼び出し](/help/authentication/user-metadata.md) および [ログアウト](/help/authentication/initiate-logout.md) サービス。


>[!TIP]
>
> **<u>ヒント：</u>** tvOS の実装については、以下の手順に従います。
 

- アプリケーションは、「*tokenSource&quot;* [ユーザーメタデータ](/help/authentication/user-metadata.md) Adobe Primetime Authentication サービスから。
- アプリケーションは、ユーザーに対し、明示的にログアウトするように指示/プロンプトを表示する必要があります *`Settings -> Accounts -> TV Provider`* tvOS の場合 **のみ** 念のため *&quot;tokenSource&quot;* 値が「」と等しい&#x200B;*Apple」*
- この申し込みは、 [ログアウトの開始](/help/authentication/initiate-logout.md) 直接 HTTP 呼び出しを使用してAdobe Primetime Authentication サービスから これは、MVPD 側でのセッションのクリーンアップを容易にしません。

 

>[!TIP]
>
> **<u>ヒント：</u>** iOS/iPadOS の実装については、以下の手順に従います。

- アプリケーションは、「*tokenSource&quot;* [ユーザーメタデータ](/help/authentication/user-metadata.md) Adobe Primetime Authentication サービスから。
- アプリケーションは、ユーザーに対し、明示的にログアウトするように指示/プロンプトを表示する必要があります *`Settings -> TV Provider`* iOS/iPadOS の場合 **のみ** 念のため *&quot;tokenSource&quot;* 値が次と等しい *&quot;Apple&quot;*.
- この申し込みは、 [ログアウトの開始](/help/authentication/initiate-logout.md) を使用してAdobe Primetime Authentication サービスから [WKWebView](https://developer.apple.com/documentation/webkit/wkwebview) または [SFSafariViewController](https://developer.apple.com/documentation/safariservices/sfsafariviewcontroller) コンポーネント。 これにより、MVPD 側でのセッションのクリーンアップが容易になります。

<!--

## Resources

- [Apple SSO Overview](/help/authentication/apple-sso-overview.md)
- [REST API Overview](/help/authentication/rest-api-overview.md)
- [REST API Cookbook (Server-to-Server)](/help/authentication/rest-api-cookbook-servertoserver.md)
- [REST API Cookbook (Client-to-Server)](/help/authentication/rest-api-cookbook-clienttoserver.md)
- [REST API Reference](/help/authentication/rest-api-reference.md)
- [Apple Developer Documentation - Video Subscriber Account Framework](https://developer.apple.com/documentation/videosubscriberaccount)
-->

