---
description: DRMを実装するには、コンテンツを暗号化するコンテンツ暗号化キーやCEK、ExpressPlayサーバーとの通信を保護するためのユーザー認証子、コンテンツ暗号化キーを識別するためのCEKSIDなど、特定の証明書とキーがキー管理システムに保存されている必要があります。
seo-description: DRMを実装するには、コンテンツを暗号化するコンテンツ暗号化キーやCEK、ExpressPlayサーバーとの通信を保護するためのユーザー認証子、コンテンツ暗号化キーを識別するためのCEKSIDなど、特定の証明書とキーがキー管理システムに保存されている必要があります。
seo-title: キー、ID、認証子
title: キー、ID、認証子
uuid: 9e5b1a64-b4e9-442f-ac15-26831aaf585d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '812'
ht-degree: 0%

---


# キー、ID、認証子{#keys-ids-and-authenticators}

DRMを実装するには、コンテンツを暗号化するコンテンツ暗号化キーやCEK、ExpressPlayサーバーとの通信を保護するためのユーザー認証子、コンテンツ暗号化キーを識別するためのCEKSIDなど、特定の証明書とキーがキー管理システムに保存されている必要があります。

保護されたコンテンツのパッケージ化、ライセンス、再生には、次のアイテムが必要です。

## コンテンツ暗号化キー{#section_8D16D36BAE3B4D1F92A0C43567D782D0}

コンテンツ暗号化キー(CEK)は、コンテンツの暗号化に使用される16バイトの文字列です。

**CEKとは何ですか。** - CEKは、パッケージャーがコンテンツの暗号化に使用するキーです。16バイトの16進エンコードされた文字列です。

**CEKはどこから来たの？**  — コンテンツプロバイダー自身が、OpenSSLやNotepad++などのツールを使用してこのキーを作成します。例：

```
openssl rand 16 -hex > cek_hex_file
```

または(AdobeOffline Packagerの場合):

1. 上記のように、または他のツールを使用して、16バイトの16進エンコードされた文字列を生成します。 次のようになります。

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Notepad++を開き、16バイトの16進文字列で貼り付けます。
1. この値をBase64エンコードして16進数のASCIIから変換し、[!DNL keyfile.bin]を作成します。 （[](../../multi-drm-workflows/quick-start/package-your-content.md)で説明します）。

**同じキー、異なる名前？** - CEKは他の場所(例：

* ** [!DNL [somefile].bin]** -AdobeOffline PackagerはCEKを[!DNL [somefile].bin]；と参照します。例：* [!DNL Keyfile.bin]* — これは、AdobeOffline Packagerで使用されるCEKで、コンテンツのパッケージ化に使用するコンピューター上のファイルの形式です。

   ランダムなCEKの16進文字列を「Base64」で囲み、ファイル（例：[!DNL keyfile.bin]）として保存します。通常は[!DNL offlinepkgr/]の下の[!DNL creds]ディレクトリに保存します。 Packagerの設定ファイル（Widevine DRM用にパッケージ化する場合は[!DNL widevine.xml]と呼び出すことができます）では、設定ファイル内のCEKを次のように参照します。

   ```
   <config>  
     <in_path>sample.mp4</in_path>  
     <out_type>dash</out_type>
     <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
     […] 
   </config> 
   ```

* **コンテンツキー**  — 呼び出し( `&contentKey=`)、エラーメッセージ、サポートチケット、その他のドキュメントでは、CEKがコンテンツキーと呼ばれる場合もあります。

**使用するタイミング/場所**

1. まず、パッケージを作成するコンピューターでCEKを使用できるようにする必要があります。 パッケージ化ツールがCEKを使用してコンテンツを暗号化します。
1. 次に、CEKを何らかの形の鍵管理システム(KMS)に格納し、各CEKを独自の[コンテンツ暗号化キー](../../multi-drm-workflows/glossary/glossary-cek.md)に関連付ける必要があります。 独自のKMSを作成するか、[ExpressPlayのキーストレージ](https://www.expressplay.com/developer/key-storage/)を使用します。 これにより、ストアフロント（ユーザーの権利付与とライセンストークンのプロビジョニングを処理するエンタイトルメントサーバー）で、実際のCEKではなく、キーIDを使用してKMSから顧客のライセンストークンを取得できます（これは非常に安全です）。

## コンテンツ暗号化キーのストレージID {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

コンテンツ暗号化キーストレージID(CEKSID)は、ビデオコンテンツの暗号化された部分を復号化するために保存されているキーを一意に識別します。

**CEKSIDとは何ですか。** - CEKSIDは、コンテンツ暗号化キー(CEK)の一意の識別子です。CEKは、保護されたコンテンツのロックを解除するために必要です。CEKSIDは、CEKが保存されている場所からCEKにアクセスするために必要です。 設定をテストする場合、ライセンスと再生の確認に同じ情報を使用すれば、パッケージ化の際にランダムなCEKSIDとCEKを指定できます。

**どこから来たの？**  — このIDは、コンテンツプロバイダーが自分で作成することも、ExpressPlayのKey  [](https://www.expressplay.com/developer/key-storage/) Storageなどのサービスを使用してCEKごとにCEKSIDを生成する（そしてCEKとCEKSIDを両方とも保存する）こともできます。また、ランダムに生成されたCEKSIDを使用したり、ビジネスモデルに合ったスキームを採用したりできます。 例えば、ランダムな16進数文字列ではなく、意味のある文字列のCEKSIDを使用できます（ID名は、件名、日付、時間などで構成できます）。

**CEKSIDの名前は？** - *コンテンツIDと呼ばれることもあります*。

## ユーザー認証子{#section_F9DDBAA54C544D82A42320CBEEB6CD74}

ユーザー認証子は、ExpressPlayで管理者アカウントを設定したときにExpressPlayで取得するキーです。 認証子は、ExpressPlayサーバーとの通信で使用されます。

**ユーザー認証子とは** - 2つのユーザー認証子は、テスト用、本番用のIDのペアを構成します。ExpressPlayは、ユーザーがサービスにサインアップすると登録します。ExpressPlayの管理ページでは、常に次の情報を利用できます。
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**使用するタイミング** - ExpressPlayサーバーへのすべての呼び出し(ライセンスサーバー、ExpressPlay Keyストレージ [](https://www.expressplay.com/developer/key-storage/)、その他の呼び出しなど)に含めます。
