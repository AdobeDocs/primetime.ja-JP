---
description: DRMを実装するには、コンテンツを暗号化するコンテンツ暗号化キーやCEK、ExpressPlayサーバーとの通信を保護するための顧客認証子、キー管理システムに保存されているコンテンツ暗号化キーを識別するCEKSIDなど、特定の証明書とキーが必要です。
seo-description: DRMを実装するには、コンテンツを暗号化するコンテンツ暗号化キーやCEK、ExpressPlayサーバーとの通信を保護するための顧客認証子、キー管理システムに保存されているコンテンツ暗号化キーを識別するCEKSIDなど、特定の証明書とキーが必要です。
seo-title: キー、ID、認証子
title: キー、ID、認証子
uuid: 9e5b1a64-b4e9-442f-ac15-26831aaf585d
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# キー、ID、認証子{#keys-ids-and-authenticators}

DRMを実装するには、コンテンツを暗号化するコンテンツ暗号化キーやCEK、ExpressPlayサーバーとの通信を保護するための顧客認証子、キー管理システムに保存されているコンテンツ暗号化キーを識別するCEKSIDなど、特定の証明書とキーが必要です。

保護されたコンテンツのパッケージ化、ライセンス、再生には、次のアイテムが必要です。

## コンテンツ暗号化キー {#section_8D16D36BAE3B4D1F92A0C43567D782D0}

コンテンツ暗号化キー(CEK)は、コンテンツの暗号化に使用される16バイトの文字列です。

**CEKとは？** - CEKは、パッケージャーがコンテンツの暗号化に使用するキーです。 16バイトの16進エンコード文字列です。

**CEKはどこから来たの？**  — このキーは、OpenSSLやNotepad++などのツールを使用して（コンテンツプロバイダーが）自分で作成します。 例：

```
openssl rand 16 -hex > cek_hex_file
```

または（Adobe Offline Packagerの場合）:

1. 上記のように、または他のツールを使用して、16バイトの16進エンコード文字列を生成します。 次のようになります。

   ```
   7debe705d938c76bfd886f077b8fa5f7
   ```

1. Notepad++を開き、16バイトの16進文字列で貼り付けます。
1. この値をBase64エンコードして16進数のASCIIから変換し、を作成します [!DNL keyfile.bin]。 (これについては、で説明し [](../../multi-drm-workflows/quick-start/package-your-content.md)ます。)

**同じキー、別の名前？** - CEKは、次のような他の場所で別の名前によって参照される場合があります。

* ** [!DNL [somefile].bin]** - Adobe Offline PackagerはCEKを[!DNL somefile [].bin]；と呼びます。例：* [!DNL Keyfile.bin]* — これは、コンテンツのパッケージ化に使用するコンピューター上のファイルの形式で、Adobe Offline Packagerで使用されるCEKです。

   ランダムなCEK 16進文字列を「Base64」にし、ファイル(例： [!DNL keyfile.bin])として保存します。通常は、下のディレクトリに [!DNL creds] あります [!DNL offlinepkgr/]。 Packagerの設定ファイル（Widevine DRM用にパッケージ化する場合など）で、次のように設定ファイル内のCEKを参照します。 [!DNL widevine.xml]

   ```
   <config>  
     <in_path>sample.mp4</in_path>  
     <out_type>dash</out_type>
     <b><key_file_path>keyfile.bin</key_file_path></b> // This is your CEK  
     […] 
   </config> 
   ```

* **コンテンツキー** — 呼び出し( `&contentKey=`)、エラーメッセージ、サポートチケット、その他のドキュメントで、CEKがコンテンツキーと呼ばれる場合もあります。

**いつ/どこで使うの？**

1. まず、パッケージを作成するコンピューターでCEKを使用できるようにする必要があります。 パッケージ化ツールは、CEKを使用してコンテンツを暗号化します。
1. 次に、CEKを何らかの形式のKey Management System(KMS)に格納し、各CEKを独自のコンテンツ暗号化キーに関連付ける必要 [があります](../../multi-drm-workflows/glossary/glossary-cek.md)。 独自のKMSを作成するか、 [ExpressPlayのKey Storageを使用します](https://www.expressplay.com/developer/key-storage/)。 これにより、ストアフロント（お客様の権利付与とライセンストークンのプロビジョニングを処理するエンタイトルメントサーバー）で、実際のCEKではなく、キーIDを使用してKMSから顧客のライセンストークンを取得できます（これは非常に安全です）。

## コンテンツ暗号化キーストレージID {#section_0C94F54970E04BDB82DE3C8A33A62CD4}

コンテンツ暗号化キーストレージID(CEKSID)は、ビデオコンテンツの暗号化された部分を復号化するために保存されたキーを一意に識別します。

**CEKSIDとは何ですか。** - CEKSIDは、コンテンツ暗号化キー(CEK)の一意の識別子です。 CEKは、保護されたコンテンツのロックを解除する必要があります。ceksidは、CEKの格納場所からCEKにアクセスするために必要です。 設定をテストする場合、ライセンスと再生の確認に同じ情報を使用する限り、パッケージ化時にランダムなCEKSIDとCEKを提供できます。

**どこから来たの？**  — このIDは、コンテンツプロバイダーが自分で作成することも、 [ExpressPlayのKey Storage](https://www.expressplay.com/developer/key-storage/) （キーストレージ）などのサービスを使用して各CEKのCEKSIDを生成（および両方を保存）することもできます。 さらに、ランダムに生成されたCEKSIDを使用したり、ビジネスモデルに適したスキームを採用したりできます。 例えば、ランダムな16進文字列ではなく意味のある文字列のCEKSIDを使用できます（ID名は、件名、日付、時間などで構成できます）。

**CEKSIDの名前は？**  — コンテンツIDと呼ばれるこ *ともあります*。

## ユーザー認証子 {#section_F9DDBAA54C544D82A42320CBEEB6CD74}

ユーザー認証子は、ExpressPlayで管理者アカウントを設定する際に取得するキーです。 認証子は、ExpressPlayサーバーとの通信で使用されます。

**顧客認証子とは何ですか。** - 2つの顧客認証子がIDのペアを構成します — 1つはテスト用、1つは実稼働用 — ExpressPlayが登録され、そのサービスに登録されます。 ExpressPlayの管理ページでは、常に次の情報を利用できます。
<!--<a id="fig_c5h_xdl_wv"></a>-->

![](assets/expressplay_admin_dashboard-web.png)

**いつ使うの？** - ExpressPlayサーバーへのすべての呼び出しに含めます。 例えば、ライセンスサーバー、 [ExpressPlay Key Storage](https://www.expressplay.com/developer/key-storage/)、その他の呼び出しなどです。
