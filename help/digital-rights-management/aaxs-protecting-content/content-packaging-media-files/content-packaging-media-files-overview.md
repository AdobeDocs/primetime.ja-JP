---
seo-title: 概要
title: 概要
uuid: 11cf1f1f-a4b2-4ac2-aae7-e925d96729d2
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# 概要 {#overview}

*パッケージ* とは、ポリシーを暗号化し、FLVまたはF4Vファイルに適用するプロセスを指します。 メディアパッケージAPIを使用して、ファイルをパッケージ化します。 Adobe Access Java SDKは、FLV、F4V、MP4など、プログレッシブダウンロードのFlashおよびAIRコンテンツのみをパッケージ化できます。 Adobe HTTP Dynamic Streaming(HDS)やApple HTTP Live Streaming(HLS)など、他のコンテンツ形式用にAdobe Access DRMを使用してコンテンツをパッケージ化するには、Adobe Media Server( [https://www.adobe.com/products/adobe-media-server-family.html](https://www.adobe.com/products/adobe-media-server-family.html))や、Adobe Broadcast SDK(https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf [](https://help.adobe.com/en_US/primetime/packagers/hdkb_api_overview_3.5.pdf))を実装するエンコーダーなど、他のツールを使用する必要があります。 また、お客様は、HDS、HLS、DASHなどの様々なターゲット形式向けにコンテンツをパッケージ化できる、アドビのJava Primetime Packagerツールセットを使用することもできます。

パッケージ化は、ライセンスサーバーから切り離されます。 パッケージャーがライセンスサーバーに接続して、コンテンツに関する情報を交換する必要はありません。 ライセンスの発行に必要な情報はすべて、コンテンツのメタデータに含まれます。

ファイルが暗号化されると、適切なライセンスがないとその内容が解析されません。 Adobe Accessでは、ファイルのどの部分を暗号化するかを選択できます。 Adobe® Access™はFLVおよびF4Vコンテンツのファイル形式を解析できるので、ファイル全体ではなく、ファイルの一部をインテリジェントに暗号化できます。 メタデータやキューポイントなどのデータは、検索エンジンがファイルを検索できるように、暗号化されないままにしておくことができます。

特定のコンテンツに複数のポリシーを設定することができます。 これは、例えば、複数回コンテンツをパッケージ化することなく、異なるビジネスモデルのコンテンツのライセンスを取得する場合に便利です。 例えば、短期間の匿名アクセスを許可し、その後顧客がコンテンツを購入し、無制限のアクセスを許可することができます。 複数のポリシーを使用してコンテンツをパッケージ化する場合、ライセンスサーバーは、ライセンスの発行に使用するポリシーを選択するロジックを実装する必要があります。

>[!NOTE] {class=&quot;- topic/note &quot;}
>
>このアーキテクチャにより、コンテンツをパッケージ化する際に、使用ポリシーを指定し、コンテンツに連結することができます。 クライアントがコンテンツを再生する前に、クライアントはそのコンピューターのライセンスを取得する必要があります。 ライセンスでは、適用される使用規則を指定し、コンテンツの復号化に使用されるキーを提供します。 このポリシーはライセンスを生成するためのテンプレートですが、ライセンスサーバは、ライセンスを発行する際に使用規則を上書きするように選択する場合があります。 ライセンスは、有効期限や再生ウィンドウなどの制約によって無効になる場合があります。

コンテンツをパッケージ化する際には、多数のオプションを使用できます。 これらは、インターフェイスと、 `DRMParameters` そのインターフェイスを実装するクラス（および）で指定 `F4VDRMParameters` されま `FLVDRMParameters`す。 これらのクラスを使用して、署名とキーのパラメーターを設定し、オーディオコンテンツ、ビデオコンテンツまたはスクリプトデータを暗号化するかどうかを指定できます。 リファレンス実装での実装方法について詳しくは、『Adobe Access Reference Implementationsの使用』で説明されているMedia Packagerのコマンドラインオプションの説 *明を参照してください*。 これらのオプションはJava APIに基づいているので、プログラム的に使用できます。

パッケージのオプションは次のとおりです。

* 暗号化オプション（オーディオ、ビデオ、部分的な暗号化）。
* ライセンスサーバのURL（クライアントは、このURLをライセンスサーバに送信されるすべての要求のベースURLとして使用します）
* ライセンスサーバートランスポート証明書
* CEKの暗号化に使用するライセンスサーバー証明書。
* メタデータに署名するPackagerの資格情報

Adobe Accessは、CEKに渡すAPIを提供します。 CEKが指定されていない場合、SDKはランダムに生成します。 通常、コンテンツの各部分に異なるCEKが必要です。 ただし、ダイナミックストリーミングでは、そのコンテンツのすべてのファイルに同じCEKを使用する可能性が高いので、ユーザーは1つのライセンスのみを必要とし、ビットレート間でシームレスに移行できます。 同じキーとライセンスを複数のコンテンツで使用するには、同じオブジェクトをに渡すか、 `DRMParameters` またはを使 `MediaEncrypter.encryptContent()`用してCEKで渡します `V2KeyParameters.setContentEncryptionKey()`。 コンテンツの各部分に異なるキーとライセンスを使用するには、各ファイルに新しいインスタ `DRMParameters` ンスを作成します。

キー回転を使用してコンテンツをパッケージ化する場合、使用する回転キーとキーの変更頻度を制御できます。 `F4VDRMParameters` インターフ `FLVDRMParameters` ェイスを実装 `KeyRotationParameters` します。 このインターフェイスを使用して、キーの回転を有効にできます。 また、を指定する必要がありま `RotatingContentEncryptionKeyProvider`す。 暗号化された各サンプルに対して、このクラスは使用する回転キーを決定します。 独自のプロバイダーを実装するか、SDKに含まれるプロバイ `TimeBasedKeyProvider` ダーを使用することができます。 この実装では、指定した秒数の後に新しいキーをランダムに生成します。

場合によっては、コンテンツのメタデータを別のファイルとして保存し、コンテンツとは別にクライアントが使用できるようにする必要があります。 これを行うには、を呼び出し、 `MediaEncrypter.encryptContent()`オブジェクトを返 `MediaEncrypterResult` します。 を呼び出 `MediaEncrypterResult.getKeyInfo()` し、結果をにキャストしま `V2KeyStatus`す。 次に、コンテンツのメタデータを取得し、ファイルに保存します。

これらのタスクはすべてJava APIを使用して実行できます。 この章で説明するJava APIについて詳しくは、『 *Adobe Access APIリファレンス』を参照してください*。

Media Packagerのリファレンス実装について詳しくは、『Adobe Access Reference Implementations *の使用』を参照してください*。
