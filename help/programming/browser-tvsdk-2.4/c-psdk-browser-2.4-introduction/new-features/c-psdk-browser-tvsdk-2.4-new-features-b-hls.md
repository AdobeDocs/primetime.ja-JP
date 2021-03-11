---
description: ブラウザーTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数のHLS機能をサポートしています。
title: サポートされるHLS機能
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '736'
ht-degree: 0%

---


# サポートされるHLS機能{#supported-hls-features}

ブラウザーTVSDKは、ビデオアプリケーションに機能を追加するために実装できる多数のHLS機能をサポートしています。

* [HLSコア再生](#hls-core-playback)
* [HLS高度な再生機能](#hls-advanced-playback)
* [HLSコンテンツ保護機能](#hls-content-protection)
* [HLSコア広告挿入機能](#hls-core-ad-insertion)
* [HLSの高度な広告挿入機能](#hls-advanced-ad-insertion)
* [HLS統合](#hls-integrations)

>[!TIP]
>
>以下の機能マトリクスの表で、![サポートされているアイコン](assets/supported15.png)は、この機能が現在のリリースでサポートされていることを意味します。

>[!TIP]
>
>Safari列の「Platform Limition」では、そのプラットフォームではサポートが実装されないので、使用事例がサポートされないことを意味します。 挿入の場合は、SSAIを使用します。 再生に関する制限が重要な場合は、プラットフォームが広告挿入の使用例をサポートするまで、SafariでのFlashへのフォールバックを強制します。

<!--<a id="section_9FB9193D5763448CB228B96164661738"></a>-->

次の機能がサポートされています。

<!-- 

Removed Nielsen row 
<table id="table_D9E2D82992554905A0A551CC71AFA189"> 
 <title>HLS integrations</title> 
 <tgroup cols="6"> 
  <colspec colnum="1" colname="col1" colwidth="*" /> 
  <colspec colnum="2" colname="col2" colwidth="*" /> 
  <colspec colnum="3" colname="col3" colwidth="*" /> 
  <colspec colnum="4" colname="col4" colwidth="*" /> 
  <colspec colnum="5" colname="col5" colwidth="*" /> 
  <colspec colnum="6" colname="col7" colwidth="*" /> 
  <thead> 
   <tr> 
    <th colname="col1" morerows="1" class="entry"> Category </th> 
    <th colname="col2" morerows="1" class="entry"> Content type </th> 
    <th colname="col3" morerows="1" class="entry"> Feature </th> 
    <th colname="col4" morerows="1" class="entry"> Flash </th> 
    <th namest="col5" nameend="col7" class="entry"> HTML5 </th> 
   </tr> 
   <tr> 
    <th colname="col5" class="entry"> FF, IE, Chrome, Android Chrome </th> 
    <th colname="col7" class="entry"> Safari, iOS Safari </th> 
   </tr> 
  </thead> 
  <tbody> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Adobe Analytics VHL integration </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
   <tr> 
    <td colname="col1"> Integrations </td> 
    <td colname="col2"> VOD + Live </td> 
    <td colname="col3"> Nielsen support </td> 
    <td colname="col4">![supported icon](assets/supported15.png) </td> 
    <td colname="col5">![supported icon](assets/supported15.png) </td> 
    <td colname="col7">![supported icon](assets/supported15.png) </td> 
   </tr> 
  </tbody> 
 </tgroup> 
</table>

 -->

## HLS統合{#hls-integrations}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 統合 | VOD + Live | Adobe AnalyticsVHL統合 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |

## HLSの高度な広告挿入機能(CSAI) {#hls-advanced-ad-insertion}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD | 広告のみ | 非対応 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | ターゲット設定パラメーター | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | カスタム広告ポリシー | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| Ad Insertion | VOD + Live | 遅延広告読み込み | ![サポートアイコン](assets/supported15.png) | 非対応 | プラットフォームの制限 |
| Ad Insertion | VOD | コンパニオン広告、バナー広告、クリック可能な広告 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| Ad Insertion | VOD | VPAID 2.0 | SWF | JavaScript | JavaScript |

## HLSコア広告挿入機能(CSAI) {#hls-core-ad-insertion}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| Ad Insertion | VOD + Live | プリロール | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | ミッドロール | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| Ad Insertion | VOD + Live | ポストロール | VODのみ | VODのみ | VODのみ |
| Ad Insertion | FER VOD | 広告の解像度と動作 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| Ad Insertion | VOD + Live | デフォルトの広告ポリシー | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| Ad Insertion | VOD + Live | VAST 2.0/3.0 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | VMAP 1.0 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| Ad Insertion | VOD + Live | CRS v3.1 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |

## HLSコンテンツ保護機能{#hls-content-protection}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| コンテンツ保護 | VOD + Live | AES-128 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| コンテンツ保護 | VOD + Live | Sample-AES | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| コンテンツ保護 | VOD | DRM | Adobeアクセス | 非対応 | FairPlay |

## HLS高度な再生機能{#hls-advanced-playback}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | VOD | オフセットでの再生 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD | オーディオのみの再生 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD | トリック再生 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD | スムーズなトリック再生 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | ID3の解析 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | 非対応 |
| 再生 | VOD + Live | 不連続マーカのサポート | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | トークン化されたストリーム | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 請求 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | Browserify | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |

## HLSコア再生{#hls-core-playback}

| カテゴリ | コンテンツタイプ | 機能 | Flash | HTML5:FF、IE、Chrome、Android Chrome | HTML5:Safari、iOS Safari |
|--- |--- |--- |--- |--- |--- |
| 再生 | VOD + Live | 一般再生（再生、一時停止、シーク） | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | FER VOD | 一般再生（再生、一時停止、シーク） | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 可変ビットレート | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 608/708キャプション | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | WebVTT | ![サポートアイコン](assets/supported15.png) | VODのみ | VODのみ |
| 再生 | VOD + Live | マニフェストのフェイルオーバー | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) |
| 再生 | VOD + Live | 高度なフェイルオーバー | ![サポートアイコン](assets/supported15.png) | VODのみ | プラットフォームの制限 |
| 再生 | VOD + Live | QoSおよびプレイヤー通知 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | 限定的なQoSサポート |
| 再生 | VOD + Live | cookieヘッダーのサポート | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | バッファー制御パラメーターの設定 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 可変ビットレートコントロールの設定 | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | カスタムタグ | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 遅延バインディングオーディオ | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |
| 再生 | VOD + Live | 302リダイレクト | ![サポートアイコン](assets/supported15.png) | ![サポートアイコン](assets/supported15.png) | プラットフォームの制限 |