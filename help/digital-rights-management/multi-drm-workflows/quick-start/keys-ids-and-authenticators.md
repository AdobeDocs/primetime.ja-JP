---
description: DRM を実装するには、コンテンツを暗号化するコンテンツ暗号化キーや CEK、ExpressPlay サーバーとの通信を保護するための顧客認証子、鍵管理システムに保存されているコンテンツ暗号化キーを識別するための CEKSID など、特定の証明書とキーが必要です。
title: キー、ID、認証子
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# キー、ID、認証子{#keys-ids-and-authenticators}

DRM を実装するには、コンテンツを暗号化するコンテンツ暗号化キーや CEK、ExpressPlay サーバーとの通信を保護するための顧客認証子、鍵管理システムに保存されているコンテンツ暗号化キーを識別するための CEKSID など、特定の証明書とキーが必要です。

保護されたコンテンツのパッケージ化、ライセンス、再生には、次の項目が必要です。

## コンテンツ暗号化キー {#section_8D16D36BAE3B4D1F92A0C43567D782D0}

コンテンツ暗号化キー (CEK) は、コンテンツの暗号化に使用される 16 バイトの文字列です。

**CEK とは** - CEK は、パッケージャーがコンテンツの暗号化に使用するキーです。 16 バイトの 16 進エンコードされた文字列です。

**CEK はどこから来たの？** - OpenSSL や Notepad++などのツールを使用して、自分（コンテンツプロバイダー）がこのキーを作成します。 例：

```
openssl rand 16 -hex > cek_hex_file
```

または (AdobeOffline Packager の場合 ):

1. 上記のように、または他のツールを使用して、16 バイトの 16 進エンコードされた文字列を生成します。 次のようになります。

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Notepad++を開き、16 バイトの 16 進文字列を貼り付けます。
1. この値を Base64 エンコードして 16 進数の ASCII から変換し、 [!DNL keyfile.bin]. ( これについては、 [](../../multi-drm-workflows/quick-start/package-your-content.md).)

**同じキー、異なる名前？**  — はい、CEK は、次のような他の場所で他の名前で参照される場合があります。

* ** [!DNL [somefile].bin]** -Adobeオフラインパッケージャーは、CEK を [!DNL [somefile].bin]；例：* [!DNL Keyfile.bin]* — これは、Adobeオフラインパッケージャが使用する CEK で、コンテンツのパッケージ化に使用するマシン上のファイルの形式です。

  ランダムな CEK の 16 進文字列を「Base64」として、ファイル ( 例： [!DNL keyfile.bin]) の場合、通常は [!DNL creds] の下のディレクトリ [!DNL offlinepkgr/]. Packager 設定ファイル内で、 [!DNL widevine.xml] （Widevine DRM 用にパッケージ化する場合）、設定ファイル内の CEK を次のように参照します。

  ```
  <config>  
    <in_path>sample.mp4</in_path>  
    <out_type>dash</out_type>
    <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
    […] 
  </config> 
  ```

* **コンテンツキー** - CEK は呼び出し ( `&contentKey=`)、エラーメッセージ、サポートチケット、その他のドキュメントなど。

**使用するタイミング/場所**

1. まず、パッケージを行うマシンで CEK を使用可能にする必要があります。 パッケージツールは、CEK を使用してコンテンツを暗号化します。
1. 次に、CEK を何らかの形式の鍵管理システム (KMS) で保存し、各 CEK を独自の CEK に関連付ける必要があります [コンテンツ暗号化キー](../../multi-drm-workflows/glossary/glossary-cek.md). 独自の KMS を作成するか、 [ExpressPlay のキーストレージ](https://www.expressplay.com/developer/key-storage/). これにより、ストアフロント（顧客の使用権限とライセンストークンのプロビジョニングを処理する権利付与サーバー）は、実際の CEK ではなくキー ID を使用して、KMS から顧客のライセンストークンを取り出すことができます（これははるかに安全です）。

## コンテンツ暗号化キーストレージ ID {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

コンテンツ暗号化キーストレージ ID(CEKSID) は、暗号化されたビデオコンテンツを復号化する格納済みのキーを一意に識別します。

**CEKSID とは** - CEKSID は、コンテンツ暗号化キー (CEK) の一意の識別子です。 CEK は、保護されたコンテンツのロックを解除するために必要です。CEKSID は、そのコンテンツが保存されている CEK にアクセスするために必要です。 設定をテストする場合、ライセンスと再生の確認に同じ情報を使用している限り、パッケージ化時にランダムな CEKSID と CEK を指定できます。

**どこから来たの？**  — 自分（コンテンツプロバイダー）がこの ID を自分で作成することも、 [ExpressPlay のキーストレージ](https://www.expressplay.com/developer/key-storage/) ：各 CEK に対して CEKSID を生成します（また、両方を保存します）。 さらに、ランダムに生成された CEKSID を使用したり、ビジネスモデルに適したスキームを採用したりできます。 例えば、ランダムな 16 進数文字列ではなく、意味のある文字列である CEKSID を使用できます（ID 名は、件名、日付、時刻などで構成できます）。

**CEKSID の他の名称は何ですか。**  — これは、 *コンテンツ ID*.

## ユーザー認証子 {#section_F9DDBAA54C544D82A42320CBEEB6CD74}

ユーザー認証子は、ExpressPlay で管理者アカウントを設定する際に ExpressPlay から取得するキーです。 認証子は、ExpressPlay サーバーとの通信で使用されます。

**ユーザー認証子とは何ですか。** - 2 人の顧客認証子は、サービスにサインアップする際に ExpressPlay が登録する ID のペア（テスト用、実稼動用）を構成します。 ExpressPlay の管理ページでは、常に利用できます。
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**使用するタイミング** - ExpressPlay サーバー（ライセンスサーバーなど）へのすべての呼び出しに含めます。 [ExpressPlay キーストレージ](https://www.expressplay.com/developer/key-storage/)、およびその他の呼び出し。
