---
description: TVSDKの機能は、設定によって動作し、MediaPlayerを介して実装されます。
seo-description: TVSDKの機能は、設定によって動作し、MediaPlayerを介して実装されます。
seo-title: 設定情報をMediaPlayerに渡して機能マネージャを作成する
title: 設定情報をMediaPlayerに渡して機能マネージャを作成する
uuid: 106ececd-a670-4360-b000-a31fec65233c
translation-type: tm+mt
source-git-commit: 31b6cad26bcc393d731080a70eff1c59551f1c8e
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---


# 設定情報をMediaPlayer {#creating-feature-managers-by-passing-configuration-information-to-the-mediaplayer}に渡して機能マネージャを作成する

TVSDKの機能は、設定によって動作し、MediaPlayerを介して実装されます。

* 設定は、ABRコントロールの初期ビットレートやデフォルトのクローズドキャプションの表示など、機能に対する特定の設定のリストです。

   機能マネージャは、機能の動作を決定するために、設定を取得する必要があります。

   Primetimeリファレンスの実装では、設定は共有の環境設定に保存されますが、環境にとって意味のある方法で設定を保存することができます。

* `MediaPlayer` は、ビデオリソースを含むTVSDKのメディアプレイヤーオブジェクトです。

   機能マネージャーは、TVSDKイベントリスナーをこのプレーヤーオブジェクトに登録し、再生セッションからデータを取得して、TVSDK機能を再生セッションにトリガーします。

各機能には、対応する設定インターフェイスがあります。 例えば、`CCManager`は`ICCConfig`を使用して設定を取得します。 `ICCConfig` には、クローズドキャプションに関連する設定情報のみを取得するメソッドが含まれます。

次の例は、`MediaPlayer`からクローズドキャプションの表示、フォントスタイル、フォントエッジに関する情報を受け取るように設定された[!DNL ICCConfig.java]ファイルを示しています。

```java
// Constructor of CCManager 
 
<b>public CCManager(ICCConfig ccConfig, MediaPlayer mediaPlayer) {...}</b> 
  
// ICCConfig methods 
 
<b>public interface ICCConfig {</b> 
  
    /** 
     * Get the closed captioning visibility config 
     * 
     * @return true if visibility is set to true, false otherwise 
     */ 
    
<b> public boolean getCCVisibility();</b> 
  
    /** 
     * Get the closed captioning font style 
     * 
     * @return TextFormat.Font object represents font style 
     */ 
     
<b>public TextFormat.Font getCCFont();</b>

    /** 
     * Get the closed captioning font edge 
     * 
     * @return TextFormat.FontEdge represents of font edge 
     */ 
     
<b>public TextFormat.FontEdge getCCFontEdge();</b> 
... 
}
```

TVSDK機能を使用するアプリケーションは、設定プロバイダーと`MediaPlayer`オブジェクトを持つ機能マネージャーを作成できます。 例：

```java
// This application needs to use the advertising workflow feature 
AdsManager adsManager = new AdsManagerOn();
```

機能マネージャ設定APIドキュメント：[Javadoc](https://help.adobe.com/en_US/primetime/api/reference_implementation/android/javadoc/com/adobe/primetime/reference/config/package-summary.html)