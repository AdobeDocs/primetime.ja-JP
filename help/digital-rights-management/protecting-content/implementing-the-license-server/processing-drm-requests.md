---
title: Adobe Primetime DRM 要求の処理
description: Adobe Primetime DRM 要求の処理
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Adobe Primetime DRM 要求の処理 {#process-adobe-primetime-drm-requests}

リクエストを管理する一般的なアプローチは、ハンドラーを作成し、リクエストを解析し、応答データまたはエラーコードを設定して、ハンドラーを閉じることです。

単一のリクエスト/応答のインタラクションを処理するために使用される基本クラスは、 `com.adobe.flashaccess.sdk.protocol.MessageHandlerBase`. のインスタンス `HandlerConfiguration` クラスは、ハンドラーを初期化するために使用されます。 `HandlerConfiguration` 転送資格情報、タイムスタンプの許容値、ポリシーの更新リスト、失効リストを含むサーバーの構成情報を格納します。ハンドラーは、要求データを読み取り、要求を解析して、 `RequestMessageBase`. 呼び出し元は、リクエスト内の情報を調べ、エラーを返すか、正常な応答を返すかを決定できます ( `RequestMessageBase` 応答データを設定する方法を提供する。)

リクエストが成功した場合は、応答データを設定します。成功しなかった場合は、を呼び出します。 `RequestMessageBase.setErrorData()` 失敗した場合。 常に、 `close()` メソッド ( `close()` 呼び出される `finally` ブロック `try` ステートメント )。 詳しくは、 `MessageHandlerBase` API リファレンスドキュメントを参照してください。

>[!NOTE]
>
>HTTP ステータスコード 200(OK) は、ハンドラーによって処理されるすべての要求に応じて送信される必要があります。 サーバーエラーが原因でハンドラーを作成できなかった場合、サーバーは 500（内部サーバーエラー）など別のステータスコードで応答する場合があります。

クライアントは、パッケージ化時に指定されたライセンスサーバ URL を、ライセンスサーバに送信されるすべての要求のベース URL として使用します。 例えば、サーバー URL が &lt;[!DNL ht<span></span>tps://licenseserver.com/path]> の場合、クライアントは &lt;[!DNL ht<span></span>tps://licenseserver.com/path/flashaccess/...]/各タイプのリクエストで使用される特定のパスの詳細については、次の節を参照してください。 ライセンスサーバーを実装する場合は、サーバーが要求のタイプごとに必要なパスに応答していることを確認してください。

ライセンスリクエストには、認証トークンを含めることができます。 ユーザー名/パスワード認証を使用した場合、リクエストには `AuthenticationToken` 生成元 `AuthenticationHandler`、および SDK は、ライセンスを発行する前に、トークンが有効であることを確認します。

## マシン識別子を使用 {#use-machine-identifiers}

すべてのAdobe Primetime DRM リクエスト（FMRMS 互換性をサポートするリクエストを除く）には、個別化時にクライアントに発行されたマシントークンに関する情報が含まれます。 マシントークンには、マシン ID が含まれます。これは、個別化中に割り当てられた識別子です。 この識別子を使用して、ユーザーがライセンスを要求した、またはドメインに参加したマシンの数をカウントできます。

次のように識別子を使用できます。

* The `getUniqueId()` メソッドは、個別化の際にデバイスに割り当てられた文字列を返します。 文字列をデータベースに格納し、識別子で検索できます。 ただし、ユーザーが HDD を再フォーマットし、再び個別化すると、この識別子が変更されます。 また、同じマシン上の異なるブラウザーでのAdobe AIRとAdobeFlash Playerの値も、この識別子の値が異なります。
* マシンをより正確に数えたい場合は、 `getBytes()` を使用して、識別子全体を保存します。 マシンが以前に認識されたかどうかを判断するには、ユーザー名のすべての識別子を取得し、を呼び出します。 `matches()` 一致するかどうかを確認します。 これは、 `matches()` メソッドは、 `MachineId.getBytes`このオプションは、比較対象の値が少数ある場合（例えば、特定のユーザーに関連付けられたマシン）にのみ実用的です。

## ユーザー認証 {#user-authentication}

Adobe Primetime DRM リクエストには、認証トークンを含めることができます。

ユーザー名/パスワード認証を使用した場合、リクエストには `AuthenticationToken` 生成元 `AuthenticationHandler`. トークンにアクセスして確認する場合は、 `RequestMessageBase.getAuthenticationToken()`. クライアントでユーザー名/パスワードリクエストを開始するには、 `DRMManager.authenticate()` ActionScriptまたはiOS API。

クライアントとサーバーがカスタム認証メカニズムを使用している場合、クライアントは他のチャネルを介して認証トークンを取得し、 `DRMManager.setAuthenticationToken` ActionScript3.0 API。 用途 `RequestMessageBase.getRawAuthenticationToken()` をクリックして、カスタム認証トークンを取得します。 サーバー実装は、カスタム認証トークンが有効かどうかを判断します。

## リプレイの保護 {#replay-protection}

再生の保護のために、 `RequestMessageBase.getMessageId()`. その場合、攻撃者は要求を再生しようとする可能性がありますが、これは拒否されるべきです。 再生の試行を検出するために、サーバーは最近表示されたメッセージ ID のリストを保存し、キャッシュされたリストに対して各受信要求を確認できます。 メッセージ識別子を保存する必要がある時間を制限するには、を呼び出します。 `HandlerConfiguration.setTimestampTolerance()`. このプロパティを設定すると、SDK は、指定された秒数を超えるサーバー時間のタイムスタンプを持つ要求を拒否します。

## ロールバック検出 {#rollback-detection}

ロールバック検出の場合、一部の使用ルールでは、権限を適用するためにクライアントが状態情報を維持する必要があります。 例えば、再生ウィンドウの使用ルールを強制するために、クライアントは、ユーザーが最初にコンテンツの表示を開始した日時を保存します。 このイベントは、トリガーウィンドウの開始を再生します。 再生ウィンドウを安全に実施するために、サーバーは、ユーザーがクライアント状態のバックアップおよび復元を行わないようにして、クライアントに保存されている再生ウィンドウの開始時間を削除する必要があります。 サーバーは、クライアントのロールバックカウンターの値を追跡することでこれを実行します。

リクエストごとに、サーバーはを呼び出すことでカウンターの値を取得します `RequestMessageBase.getClientState()` 手に入れる `ClientState` オブジェクト、次に `ClientState.getCounter()` クライアント状態カウンタの現在の値を取得する。 サーバーは、クライアントごとにこの値を保存する必要があります ( `MachineId.getUniqueId()` を呼び出して、ロールバックカウンタ値に関連付けられたクライアントを特定し、 `ClientState.incrementCounter()` を使用してカウンタ値を 1 ずつ増やします。 サーバがカウンタ値が、サーバが最後に閲覧した値より小さいことを検出した場合、クライアントの状態がロールバックされた可能性があります。

詳しくは、 `ClientState` API リファレンスドキュメントを参照してください。

## グローバルサーバー設定データ{#global-server-configuration-data}

ライセンスサーバが使用する設定に加えて、 `HandlerConfiguration` は、ライセンスの適用方法を制御するためにクライアントに送信できる構成情報を格納します。 これは、 `ServerConfigData` クラスと呼び出し `HandlerConfiguration.setServerConfigData()`. これらの設定は、このライセンスサーバーが発行したライセンスにのみ適用されます。

クロック・ウィンドバックの許容値は、ライセンス・サーバによって設定され、クライアントがライセンスを強制する方法を制御する 1 つのプロパティです。 デフォルトでは、ユーザーはライセンスを無効にすることなく、4 時間前にマシンクロックを設定できます。 ライセンスサーバーのオペレーターが別の設定を使用する場合は、新しい値を `ServerConfigData` クラス。 これらの設定の値を変更する場合は、必ず `setVersion()`. 新しい値は、クライアント上のバージョンが現在のバージョンより古い場合にのみクライアントに送信されます `ServerConfigData` バージョン。

## Crossdomain DRM ポリシーファイル {#crossdomain-drm-policy-file}

ライセンスサーバーがビデオ再生SWFとは異なるドメインでホストされている場合、クロスドメイン DRM ポリシーファイル ( [!DNL crossdomain.xml]) が必要な場合は、SWFがライセンスサーバーからライセンスを要求できるようにします。 クロスドメイン DRM ポリシーファイルは、XML ファイルで表されます。このファイルを使用すると、サーバーは、他のドメインから提供されるSWFファイルに対して、そのデータとドキュメントが使用可能であることを示すことができます。 ライセンスサーバーのクロスドメイン DRMSWFファイルで指定されたドメインから提供されたポリシーファイルは、そのライセンスサーバーのデータまたはアセットにアクセスできます。

Adobeでは、信頼されたドメインのみがライセンスサーバーにアクセスでき、Web サーバー上のライセンスサブディレクトリへのアクセスを制限することで、クロスドメインポリシーファイルを展開する際に、開発者はベストプラクティスに従うことをお勧めします。

クロスドメイン DRM ポリシーファイルの詳細については、次の場所を参照してください。

* Web サイトの制御（DRM ポリシーファイル）
* クロスドメイン DRM ポリシーファイルの仕様： [https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html](https://www.adobe.com/devnet/articles/crossdomain_policy_file_spec.html)
