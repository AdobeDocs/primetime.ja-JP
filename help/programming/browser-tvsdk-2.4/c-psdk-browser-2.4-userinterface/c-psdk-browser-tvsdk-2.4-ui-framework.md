---
description: UIフレームワークは、ブラウザーTVSDKの上にあるUIレイヤーで、初期設定の様々なビデオプレーヤー関連のUI構成を提供します。 環境に適したポイントの変更を行うことで、カスタマイズ性の高いプレーヤーを作成できます。
seo-description: UIフレームワークは、ブラウザーTVSDKの上にあるUIレイヤーで、初期設定の様々なビデオプレーヤー関連のUI構成を提供します。 環境に適したポイントの変更を行うことで、カスタマイズ性の高いプレーヤーを作成できます。
seo-title: UIフレームワーク
title: UIフレームワーク
uuid: 8460d65c-b9aa-40d0-9e68-771b9f73a7b4
translation-type: tm+mt
source-git-commit: 2399515edaad49341cfa406a13887bcc8a3562be

---


# UIフレームワーク {#the-ui-framework}

UIフレームワークは、ブラウザーTVSDKの上にあるUIレイヤーで、初期設定の様々なビデオプレーヤー関連のUI構成を提供します。 環境に適したポイントの変更を行うことで、カスタマイズ性の高いプレーヤーを作成できます。

>[!TIP]
>
>視覚（スキン表示）とUIの動作をカスタマイズできます。

独自の動作を書き直すか、特定のデフォルト動作の機能を上書きすることができます。 また、SDKに付属の動作を一から書き込むことで、その動作を再利用することもできます。

## 基本プレーヤーの作成 {#section_30E4812C4DDA4B519C9C837930B6AE45}

`primetimevisualapi.min.js` はUIフレームワークライブラリで、そのすべての機能がグローバルオブジェクトptpを通じて公開されます。 次の例では、メソッドは基にな `videoPlayer` るプレーヤーを作成します。

```js
<script src="scripts/primetimevisualapi.min.js"></script> 
<script> 
    (function(){ 
        var player = ptp.videoPlayer('#video1'); 
    })(); 
</script>
```

## プレイヤーの設定 {#section_9FC936B983CD40439E6D7675197B226C}

次のいずれかの方法でプレイヤーを設定できます。

* JSONオブジェクトの使用
* APIの使用

JSONオブジェクトを生成するために、Browser TVSDKはUI Configuratorツールを提供します。 このツールでは、様々な設定を選択し、をクリックして設 **[!UICONTROL Test Configuration]** 定を確認し、をクリックして設定をダ **[!UICONTROL Download Configuration]** ウンロードすることができます。 ダウンロードしたファイルの内容は、APIに渡されるJSONオブジェクトとして使用さ `ptp.videoPlayer` れます。

**UIコンフィギュレータツールの実行方法**:

1. ブラウザーTVSDK `frameworks` で使用可能なフォルダーを、ローカルWebサーバー上でホストします。
1. ツールを開くには、ブラウザーを開いてに移動しま `< path-to-hosted-frameworks-folder>/ui-framework/ui-configurator/`す。

**プレイヤーの動作の設定**

次のいずれかの方法で、プレイヤーの動作を設定できます。

>[!TIP]
>
>一部の設定では、両方のオプションを使用できます。

* **videoBehavior APIを使用して** 、を返し `ptp.videoPlayer` ます。こ `ptp.videoBehavior`れにより、基になるビデオプレーヤーを設定できます。 再生関連の設定が必要な場合は、このオプションを使用できます。

   ```js
   player.setAbrControlParameters ({object})
   ```

* **設定オブジェクトをvideoPlayer関数に渡す** 。このオブジェクトを使用する場合は、上記の再生設定に加えて、UIの動作を設定できます。 呼び出し元は、変更する必要があるパラメーターを指定する必要があり、プレーヤーは未指定のパラメーターに対して引き続きデフォルト値を使用します。

   ```js
   var player = ptp.videoPlayer('#video1', { 
           player: { 
               abrControlParameters : {object} 
       }, 
       controlBar : {object} 
   });
   ```

   上記の例では、ABR制御パラメーターは設定オブジェクトを使用して設定されていました。 また、コントロールバーの動作を設定するためにオブジェクトが渡されました。

   設定オブジェクトの構造については、下の「設定オブジェクトの構造を表示する」の節を参照してください。

* **AdobePSDK.MediaPlayerへのアクセス** ：ブラウザーTVSDKのMediaPlayer `videoPlayer.getMediaPlayer` にアクセスする必要がある高度な使用例を特に使用できます。

* **プレイヤーのスキン表示の設定** 。プレイヤーのスキン表示について詳しくは、プレイヤーのスキン表示を参 [照してください](../../browser-tvsdk-2.4/c-psdk-browser-2.4-userinterface/c-psdk-browser-tvsdk-2.4-skin-the-player.md)。

## デフォルト動作の変更 {#section_D5D692638FFF4BEF81F7BE70E438CCE9}

UIフレームワークの用語では、動作とは、特定のコンポーネントの視覚的な部分と相互作用部分を定義する構成体です。 以下に説明するオブジェクト構造を使用して、動作を変更できます。

例えば、ボリュームスライダが表示された後、非表示にしたくない場合は、次のサンプルを使用します。

```js
var customVolumeSliderBehavior = function (element, configuration, player) { 
    function neverHide() { 
        // do nothing 
 } 
 
    var api = ptp.volumeSliderBehavior(element, configuration, player) 
        .compose({ 
            hide: neverHide 
 }); 
    return api; 
}; 
var player = ptp.videoPlayer('.videoHolder', { 
    controlBar : { 
        volume: { 
            slider: { 
                behavior: customVolumeSliderBehavior 
 } 
        } 
    } 
}
```

>[!NOTE]
>
>必要なカスタマイズに応じて、その動作の特定の機能を上書きしたり、独自の動作を作成したりできます。 上書き可能な機能について詳しくは、 [UIフレームワーク](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/index.html) APIドキュメントを参照してください。

## 参照 {#section_0A76A3F44D8A49B09FE4C83F3FACCB76}

その他の参照情報を次に示します。

* **「設定オブジェクトの構造を表示** 」これは、すべてのデフォルト動作と動作のデフォルト要素とを階層的に示す完全なオブジェクト構造です。 サンプル設定では、UIファクトリを使用して要素が作成されていました。 同じ方法を使用することも、好みの方法で要素を構築することもできます。

   変更するパーツのみを指定する必要があり、残りの機能はデフォルトから選択されます。 使用事例に応じて、を開始するには、または構造を指定する `SingleViewConfigurationObject` 必要があり `MultiViewConfigurationObject` ます。

   ```js
   var DEFAULT_CONTROL_BAR_CONFIG = { 
       behavior: ptp.controlBarBehavior, 
       element: ptp.factories.simpleDivFactory(null, ptp.elementGetter(selector), 'ptp-control-bar'), 
       audioTrack: { 
           behavior: ptp.audioTrackButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('audioTrackBtn', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-audio-track ptp-control-bar-btn') 
       }, 
       closedCaption: { 
           behavior: ptp.closedCaptionButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('cc', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ' + 
               'ptp-btn-closed-caption ptp-control-bar-btn hidden', 
               'CC') 
       }, 
       displayTime: { 
           behavior: ptp.timeRemainingBehavior, 
           element: ptp.factories.simpleDivFactory('displayTime', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-txt-control ptp-txt-display-time') 
       }, 
       fastForward: { 
           behavior: ptp.fastForwardButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('fastForward', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-fastforward ptp-control-bar-btn', 
               'Fast Forward') 
       }, 
       fastRewind: { 
           behavior: ptp.fastRewindButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('fastRewind', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-fastrewind ptp-control-bar-btn', 
               'Fast Rewind') 
       }, 
       fullScreen: { 
           behavior: ptp.fullScreenButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('fullScreen', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-fullscreen ptp-control-bar-btn', 
               'Full Screen') 
       }, 
       moreOptions: { 
           behavior: ptp.moreOptionsButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('moreOptions', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-more-options ptp-control-bar-btn', 
               'More Options') 
       }, 
       multiView: { 
           behavior: ptp.multiViewButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('multiView', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-multiview ptp-control-bar-btn', 
               'Multi View') 
       }, 
       socialButton: { 
           behavior: ptp.shareVideoButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('shareVideo', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-share-video ptp-control-bar-btn', 
               'Share Video') 
       }, 
       volume: { 
           behavior: ptp.volumeBehavior, 
           element: ptp.factories.simpleDivFactory('volume', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-volume-control ptp-control-bar-btn'), 
           mute: { 
               behavior: ptp.muteButtonBehavior, 
               element: ptp.factories.simpleButtonFactory('mute', ptp.elementGetter('.ptp-volume-control'), 
                   'ptp-control ptp-button-background ptp-btn-volume', 'Mute') 
           }, 
           slider: { 
               behavior: ptp.volumeSliderBehavior, 
               element: ptp.factories.simpleSliderFactory('volumeSlider', ptp.elementGetter('.ptp-volume-control'), 
                   'ptp-control ptp-volume-slider ptp-volume-hidden', 'Volume') 
           } 
       }, 
       pip: { 
           behavior: ptp.pipButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('pip', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-pip ptp-control-bar-btn', 'PIP') 
       }, 
       playPause: { 
           behavior: ptp.playPauseButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('play', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-playpause ptp-control-bar-btn', 
               'Play') 
       }, 
       rewind: { 
           behavior: ptp.rewindButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('rewind', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-rewind ptp-control-bar-btn', 
               'Rewind') 
       }, 
       scrubBar: { 
           element: ptp.factories.simpleDivFactory('scrubBar', ptp.elementGetter('.ptp-control-bar'), 'ptp-scrub-bar'), 
           behavior: ptp.scrubBarBehavior, 
    }, 
     bufferProgressBar: { 
               element: ptp.factories.simpleDivFactory('bufferProgressBar', ptp.elementGetter('.ptp-scrub-bar'), 
                   'ptp-buffer-progress-bar'), 
               behavior: ptp.bufferProgressBarBehavior 
     }, 
       seekToBar: { 
               element: ptp.factories.simpleDivFactory('seekToBar', ptp.elementGetter('.ptp-scrub-bar'), 'ptp-seek-to-bar'), 
               behavior: ptp.seekToBarBehavior 
     }, 
       playbackProgressBar: { 
               element: ptp.factories.simpleDivFactory('playbackProgressBar', ptp.elementGetter('.ptp-scrub-bar'), 
                   'ptp-playback-progress-bar'), 
               behavior: ptp.playProgressBarBehavior 
     }, 
       playHead: { 
               element: ptp.factories.simpleDivFactory('playHead', ptp.elementGetter('.ptp-scrub-bar'), 'ptp-progress-bar-play-head'), 
               behavior: ptp.playHeadBehavior 
     } 
       }, 
       slowRewind: { 
           behavior: ptp.slowRewindButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('slowRewind', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-slowrewind ptp-control-bar-btn', 
               'Slow Rewind'), 
           enabled: true 
    }, 
       slowForward: { 
           behavior: ptp.slowForwardButtonBehavior, 
           element: ptp.factories.simpleButtonFactory('slowForward', ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-button-background ptp-btn-slowforward ptp-control-bar-btn', 
               'Slow Forward') 
       }, 
       spacer: { 
           element: ptp.factories.simpleDivFactory('spacer', ptp.elementGetter('.ptp-control-bar'), 'ptp-fill-spacer') 
       }, 
       trickPlayRateDisplay: { 
           behavior: ptp.trickPlayRateDisplayBehavior, 
           element: ptp.factories.simpleDivFactory('trickPlayDisplay', 
               ptp.elementGetter('.ptp-control-bar'), 
               'ptp-control ptp-btn-control ptp-control-bar-trick-play-rate hidden') 
       } 
   }; 
   var DEFAULT_LOCALIZATION_CONFIG = { 
       locale: 'en-US', 
       behavior: mapLocalizer, 
       localizationMap: { 
           'en-US': { 
               OK: 'Okay', 
               CANCEL: 'Cancel', 
               DEFAULT: 'Default', 
               NONE: 'None', 
               FONT_MONO_W_SERIF: 'Monospaced With Serifs', 
               FONT_PROP_W_SERIF: 'Proportional with Serifs', 
               FONT_MONO_WO_SERIF: 'Monospaced without Serifs', 
               FONT_CASUAL: 'Casual', 
               FONT_CURSIVE: 'Cursive', 
               FONT_SMALL_CAPS: 'Small Capitals', 
               FONT_EDGE_DEFAULT: 'Default', 
               FONT_EDGE_NONE: 'None', 
               FONT_EDGE_RAISED: 'Raised', 
               FONT_EDGE_DEPRESSED: 'Depressed', 
               FONT_EDGE_UNIFORM: 'Uniform', 
               FONT_EDGE_DROP_SHADOW_LEFT: 'Drop Shadow Left', 
               FONT_EDGE_DROP_SHADOW_RIGHT: 'Drop Shadow Right', 
               SIZE_SMALL: 'Small', 
               SIZE_MEDIUM: 'Medium', 
               SIZE_LARGE: 'Large', 
               COLOR_BLACK: 'Black', 
               COLOR_GREY: 'Grey', 
               COLOR_WHITE: 'White', 
               COLOR_BRIGHT_WHITE: 'Bright White', 
               COLOR_DARK_RED: 'Dark Red', 
               COLOR_RED: 'Red', 
               COLOR_BRIGHT_RED: 'Bright Red', 
               COLOR_DARK_GREEN: 'Dark Green', 
               COLOR_GREEN: 'Green', 
               COLOR_BRIGHT_GREEN: 'Bright Green', 
               COLOR_DARK_BLUE: 'Dark Blue', 
               COLOR_BLUE: 'Blue', 
               COLOR_BRIGHT_BLUE: 'Bright Blue', 
               COLOR_DARK_YELLOW: 'Dark Yellow', 
               COLOR_YELLOW: 'Yellow', 
               COLOR_BRIGHT_YELLOW: 'Bright Yellow', 
               COLOR_DARK_MAGENTA: 'Dark Magenta', 
               COLOR_MAGENTA: 'Magenta', 
               COLOR_BRIGHT_MAGENTA: 'Bright Magenta', 
               COLOR_DARK_CYAN: 'Dark Cyan', 
               COLOR_CYAN: 'Cyan', 
               COLOR_BRIGHT_CYAN: 'Bright Cyan', 
               REPLAY: 'Replay', 
               PLAY: 'Play', 
               PAUSE: 'Pause', 
               STOP: 'Stop' 
     } 
       } 
   }; 
   var DEFAULT_AUDIO_TRACK_SELECTION_CONFIG = { 
       behavior: ptp.audioTrackSelectionPanelBehavior, 
       element: ptp.factories.simpleDivFactory('audioTrackSelectionPanel', ptp.elementGetter(selector), 
           'ptp-audio-track-selection-panel hidden'), 
       audioTrackSelectionPanelHeader: { 
           behavior: ptp.audioTrackSelectionPanelHeader, 
           element: ptp.factories.simpleDivFactory('header', ptp.elementGetter('.ptp-audio-track-selection-panel'), 
               'ptp-panel-header ptp-audio-track-selection-header'), 
           audioTrackSelectionPanelCloseButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('closeButton', ptp.elementGetter('.ptp-audio-track-selection-header'), 
                   'ptp-control ptp-btn-control ptp-panel-close-btn', 'X') 
           }, 
           audioTrackSelectionPanelTitle: { 
               element: ptp.factories.simpleDivFactory('title', ptp.elementGetter('.ptp-audio-track-selection-header'), 
                   'ptp-panel-title', 'Audio Track') 
           } 
       }, 
       audioTrackSelectionPanelSeparator: { 
           element: ptp.factories.simpleHRFactory('audioTrackSelectionPanelSeparator', 
               ptp.elementGetter('.ptp-audio-track-selection-panel'), 'ptp-hr-separator') 
       }, 
       audioTrackSelectionMenu: { 
           behavior: ptp.audioTrackSelectionMenu, 
           element: ptp.factories.simpleDivFactory('audioTrackSelectionMenu', ptp.elementGetter('.ptp-audio-track-selection-panel'), 
               'ptp-audio-track-selection-menu', 'Menu TBD') 
       } 
   }; 
   
   var DEFAULT_CLOSED_CAPTION_LANGUAGE_PANEL_CONFIG = { 
       behavior: ptp.closedCaptionLanguagePanelBehavior, 
       element: ptp.factories.simpleDivFactory('closedCaptionLanguagePanel', ptp.elementGetter(selector), 
           'ptp-closed-caption-panel hidden ptp-closed-caption-language-panel'), 
       closedCaptionLanguagePanelHeader: { 
           behavior: ptp.closedCaptionLanguagePanelHeader, 
           element: ptp.factories.simpleDivFactory('header', ptp.elementGetter('.ptp-closed-caption-language-panel'), 
               'ptp-panel-header ptp-closed-caption-language-header'), 
           closedCaptionLanguageCloseButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('closeButton', ptp.elementGetter('.ptp-closed-caption-language-header'), 
                   'ptp-control ptp-btn-control ptp-panel-close-btn', 'X') 
           }, 
           closedCaptionLanguageTitle: { 
               element: ptp.factories.simpleDivFactory('title', ptp.elementGetter('.ptp-closed-caption-language-header'), 
                   'ptp-panel-title', 'Closed Captions') 
           }, 
           closedCaptionLanguageOptionsButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('title', ptp.elementGetter('.ptp-closed-caption-language-header'), 
                   'ptp-closed-caption-options-btn', 'Options') 
           } 
       }, 
       closedCaptionLanguageSeparator: { 
           element: ptp.factories.simpleHRFactory('closedCaptionLanguageSeparator', ptp.elementGetter('.ptp-closed-caption-panel'), 
               'ptp-hr-separator') 
       }, 
       closedCaptionOptions: { 
           behavior: ptp.closedCaptionLanguageMenu, 
           element: ptp.factories.simpleDivFactory('captionLanguageMenu', ptp.elementGetter('.ptp-closed-caption-panel'), 
               'ptp-scroll-bar ptp-closed-caption-language-menu') 
       } 
   }; 
   
   var DEFAULT_CLOSED_CAPTION_OPTIONS_PANEL_CONFIG = { 
       behavior: ptp.closedCaptionOptionsPanelBehavior, 
       element: ptp.factories.simpleDivFactory('closedCaptionOptionsPanel', ptp.elementGetter(selector), 
           'ptp-closed-caption-panel hidden ptp-closed-caption-options-panel'), 
       closedCaptionOptionsHeader: { 
           behavior: ptp.closedCaptionOptionsPanelHeader, 
           element: ptp.factories.simpleDivFactory('closedCaptionOptionsHeader', ptp.elementGetter('.ptp-closed-caption-options-panel'), 
               'ptp-panel-header ptp-closed-caption-options-header'), 
           closedCaptionOptionsCloseButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('closedCaptionOptionsCloseButton', 
                   ptp.elementGetter('.ptp-closed-caption-options-header'), 
                   'ptp-control ptp-btn-control ptp-panel-close-btn', '<') 
           }, 
           closedCaptionOptionsTitle: { 
               element: ptp.factories.simpleDivFactory('closedCaptionOptionsTitle', 
                   ptp.elementGetter('.ptp-closed-caption-options-header'), 'ptp-panel-title', 'Closed Captions') 
           }, 
           closedCaptionLanguageDoneButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('closedCaptionLanguageDoneButton', 
                   ptp.elementGetter('.ptp-closed-caption-options-header'), 'ptp-closed-caption-done-btn', 'Done') 
           } 
       }, 
       closedCaptionOptionsHeaderSeparator: { 
           element: ptp.factories.simpleHRFactory('closedCaptionOptionsHeaderSeparator', 
               ptp.elementGetter('.ptp-closed-caption-options-panel'), 'ptp-hr-separator') 
       }, 
       closedCaptionOptionsMenu: { 
           behavior: ptp.closedCaptionOptionsMenu, 
           element: ptp.factories.simpleDivFactory('closedCaptionOptionsMenu', ptp.elementGetter('.ptp-closed-caption-options-panel'), 
               'ptp-closed-caption-options-menu'), 
           closedCaptionOptionsMainMenu: { 
               behavior: ptp.closedCaptionOptionsMainMenu, 
               element: ptp.factories.simpleDivFactory('closedCaptionOptionsMainMenu', 
                   ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                   'ptp-scroll-bar ptp-closed-caption-options-main-menu'), 
               closedCaptionOptionsFontStyle: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontStyle', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Font Style') 
               }, 
               closedCaptionOptionsFontSize: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontSize', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Font Size') 
               }, 
               closedCaptionOptionsFontColor: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontColor', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Font Color') 
               }, 
               closedCaptionOptionsFontOpacity: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontOpacity', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Font Opacity') 
               }, 
               closedCaptionOptionsBackgroundColor: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsBackgroundColor', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Background Color') 
               }, 
               closedCaptionOptionsBackgroundOpacity: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsBackgroundOpacity', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Background Opacity') 
               }, 
               closedCaptionOptionsFillColor: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFillColor', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Fill Color') 
               }, 
               closedCaptionOptionsFillOpacity: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFillOpacity', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Fill Opacity') 
               }, 
               closedCaptionOptionsFontEdge: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontEdge', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Stroke Weight') 
               }, 
               closedCaptionOptionsFontEdgeColor: { 
                   behavior: ptp.buttonBehavior, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontEdgeColor', 
                       ptp.elementGetter('.ptp-closed-caption-options-main-menu'), 
                       'ptp-closed-caption-options-menu-item', 'Stroke Color') 
               } 
           }, 
           closedCaptionOptionsMenuSeparator: { 
               element: ptp.factories.simpleHRFactory('closedCaptionOptionsMenuSeparator', 
                   ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                   'ptp-closed-caption-options-menu-separator') 
           }, 
           closedCaptionOptionsSubMenu: { 
               behavior: ptp.closedCaptionOptionsSubMenu, 
               closedCaptionOptionsFontStyleSubMenu: { 
                   behavior: ptp.verticalListMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontStyleSubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-scroll-bar ptp-closed-caption-options-sub-menu hidden') 
               }, 
               closedCaptionOptionsFontEdgeSubMenu: { 
                   behavior: ptp.verticalListMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontEdgeSubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-scroll-bar ptp-closed-caption-options-sub-menu hidden') 
               }, 
               closedCaptionOptionsFontEdgeColorSubMenu: { 
                   behavior: ptp.verticalListMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontEdgeColorSubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-scroll-bar ptp-closed-caption-options-sub-menu hidden') 
               }, 
               closedCaptionOptionsFontSizeSubMenu: { 
                   behavior: ptp.verticalListMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontSizeSubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-scroll-bar ptp-closed-caption-options-sub-menu hidden') 
               }, 
               closedCaptionOptionsFontColorSubMenu: { 
                   behavior: ptp.verticalListMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontColorSubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-scroll-bar ptp-closed-caption-options-sub-menu hidden') 
               }, 
               closedCaptionOptionsFontOpacitySubMenu: { 
                   behavior: ptp.sliderMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFontOpacitySubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-closed-caption-options-sub-menu ptp-closed-caption-options-opacity-slider hidden') 
               }, 
               closedCaptionOptionsBackgroundColorSubMenu: { 
                   behavior: ptp.verticalListMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsBackgroundColorSubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-scroll-bar ptp-closed-caption-options-sub-menu hidden') 
               }, 
               closedCaptionOptionsBackgroundOpacitySubMenu: { 
                   behavior: ptp.sliderMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsBackgroundOpacitySubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-closed-caption-options-sub-menu ptp-closed-caption-options-opacity-slider hidden') 
               }, 
               closedCaptionOptionsFillColorSubMenu: { 
                   behavior: ptp.verticalListMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFillColorSubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-scroll-bar ptp-closed-caption-options-sub-menu hidden') 
               }, 
               closedCaptionOptionsFillOpacitySubMenu: { 
                   behavior: ptp.sliderMenu, 
                   element: ptp.factories.simpleDivFactory('closedCaptionOptionsFillOpacitySubMenu', 
                       ptp.elementGetter('.ptp-closed-caption-options-menu'), 
                       'ptp-closed-caption-options-sub-menu ptp-closed-caption-options-opacity-slider hidden') 
               } 
           } 
       }, 
       closedCaptionOptionsPreviewSeparator: { 
           element: ptp.factories.simpleHRFactory('closedCaptionOptionsPreviewSeparator', 
               ptp.elementGetter('.ptp-closed-caption-options-panel'), 'ptp-hr-separator') 
       }, 
       closedCaptionPreviewPanel: { 
           behavior: ptp.closedCaptionPreviewPanel, 
           text: 'Sample Captions', 
           element: ptp.factories.simpleDivFactory('closedCaptionPreviewPanel', 
               ptp.elementGetter('.ptp-closed-caption-options-panel'), 
               'ptp-closed-caption-preview-panel', 'Sample Captions') 
       }, 
       closedCaptionOptionsFooterSeparator: { 
           element: ptp.factories.simpleHRFactory('closedCaptionOptionsFooterSeparator', 
               ptp.elementGetter('.ptp-closed-caption-options-panel'), 'ptp-hr-separator') 
       }, 
       closedCaptionOptionsFooter: { 
           behavior: ptp.closedCaptionOptionsFooter, 
           element: ptp.factories.simpleDivFactory('closedCaptionOptionsFooter', 
               ptp.elementGetter('.ptp-closed-caption-options-panel'), 'ptp-closed-caption-options-footer'), 
           closedCaptionOptionsResetButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('closedCaptionOptionsResetButton', 
                   ptp.elementGetter('.ptp-closed-caption-options-footer'), 
                   'ptp-closed-caption-options-reset-button', 'Reset to Default') 
           }, 
           closedCaptionOptionsApplyButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('closedCaptionOptionsApplyButton', 
                   ptp.elementGetter('.ptp-closed-caption-options-footer'), 
                   'ptp-closed-caption-options-apply-button', 'Apply') 
           } 
       } 
   }; 
   
   var DEFAULT_SHARE_VIDEO_PANEL_CONFIG = { 
       behavior: ptp.shareVideoPanelBehavior, 
       element: ptp.factories.simpleDivFactory('shareVideoPanel', ptp.elementGetter(selector), 'ptp-share-video-panel hidden'), 
       shareVideoPanelHeader: { 
           behavior: ptp.shareVideoPanelHeader, 
           element: ptp.factories.simpleDivFactory('shareVideoPanelHeader', ptp.elementGetter('.ptp-share-video-panel'), 
               'ptp-panel-header ptp-share-video-panel-header'), 
           shareVideoPanelCloseButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('shareVideoPanelCloseButton', ptp.elementGetter('.ptp-share-video-panel-header'), 
                   'ptp-control ptp-btn-control ptp-panel-close-btn', 'X') 
           }, 
           shareVideoPanelTitle: { 
               element: ptp.factories.simpleDivFactory('shareVideoPanelTitle', ptp.elementGetter('.ptp-share-video-panel-header'), 
                   'ptp-panel-title', 'Social Share') 
           } 
       }, 
       shareVideoPanelHeaderSeparator: { 
           element: ptp.factories.simpleHRFactory('shareVideoPanelHeaderSeparator', ptp.elementGetter('.ptp-share-video-panel'), 
               'ptp-hr-separator') 
       }, 
       shareVideoPanelMenu: { 
           element: ptp.factories.simpleDivFactory('shareVideoPanelMenu', ptp.elementGetter('.ptp-share-video-panel'), 
               'share-video-panel-menu'), 
           behavior: ptp.shareVideoPanelMenu, 
           shareVideoPanelFacebookBtn: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('shareVideoPanelFacebookBtn', ptp.elementGetter('.share-video-panel-menu'), 
                   'ptp-btn-control ptp-button-background ptp-share-video-panel-menu-item ' + 
                   'ptp-btn-share-video-facebook') 
           }, 
           shareVideoPanelTwitterBtn: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('shareVideoPanelTwitterBtn', ptp.elementGetter('.share-video-panel-menu'), 
                   'ptp-btn-control ptp-button-background ptp-share-video-panel-menu-item ' + 
                   'ptp-btn-share-video-twitter') 
           }, 
           shareVideoPanelGoogleBtn: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('shareVideoPanelGoogleBtn', ptp.elementGetter('.share-video-panel-menu'), 
                   'ptp-btn-control ptp-button-background ptp-share-video-panel-menu-item ' + 
                   'ptp-btn-share-video-google-plus') 
           }, 
           shareVideoPanelLinkedinBtn: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('shareVideoPanelLinkedinBtn', ptp.elementGetter('.share-video-panel-menu'), 
                   'ptp-btn-control ptp-button-background ptp-share-video-panel-menu-item ' + 
                   'ptp-btn-share-video-linkedin') 
           } 
       } 
   }; 
   
   var DEFAULT_MORE_OPTIONS_CONTROL_PANEL_CONFIG = { 
       behavior: ptp.moreOptionsControlPanel, 
       element: ptp.factories.simpleDivFactory('moreOptionsControlPanel', ptp.elementGetter(selector), 
           'ptp-more-options-control-panel hidden'), 
       moreOptionsControlPanelHeader: { 
           behavior: ptp.moreOptionsControlPanelHeader, 
           element: ptp.factories.simpleDivFactory('moreOptionsControlPanelHeader', 
               ptp.elementGetter('.ptp-more-options-control-panel'), 
               'ptp-panel-header ptp-more-options-control-panel-header'), 
           moreOptionsControlPanelCloseButton: { 
               behavior: ptp.buttonBehavior, 
               element: ptp.factories.simpleDivFactory('moreOptionsControlPanelCloseButton', 
                   ptp.elementGetter('.ptp-more-options-control-panel-header'), 
                   'ptp-control ptp-btn-control ptp-panel-close-btn', 'X') 
           }, 
           moreOptionsControlPanelTitle: { 
               element: ptp.factories.simpleDivFactory('moreOptionsPanelTitle', 
                   ptp.elementGetter('.ptp-more-options-control-panel-header'), 
                   'ptp-panel-title', 'Options') 
           } 
       }, 
       moreOptionsPanelHeaderSeparator: { 
           element: ptp.factories.simpleHRFactory('moreOptionsPanelHeaderSeparator', 
               ptp.elementGetter('.ptp-more-options-control-panel'), 
               'ptp-hr-separator') 
       }, 
       moreOptionsPanelMenu: { 
           element: ptp.factories.simpleDivFactory('moreOptionsPanelMenu', 
               ptp.elementGetter('.ptp-more-options-control-panel'), 
               'ptp-more-options-control-panel-menu'), 
           behavior: ptp.moreOptionsControlPanelMenu, 
           audioTrackButton: { 
               behavior: ptp.audioTrackButtonBehavior, 
               element: ptp.factories.simpleButtonFactory('audioTrackBtn', ptp.elementGetter('.ptp-more-options-control-panel-menu'), 
                   'ptp-control ptp-btn-control ptp-button-background ptp-btn-audio-track ' + 
                   'ptp-more-options-control-panel-menu-item ' + 
                   'ptp-more-options-menu-btn', 
                   'Audio Track') 
           }, 
           multiViewButton: { 
               behavior: ptp.multiViewButtonBehavior, 
               element: ptp.factories.simpleButtonFactory('multiView', ptp.elementGetter('.ptp-more-options-control-panel-menu'), 
                   'ptp-control ptp-btn-control ptp-button-background ptp-btn-multiview ' + 
                   'ptp-more-options-control-panel-menu-item ' + 
                   'ptp-more-options-menu-btn', 
                   'Multi View') 
           }, 
           pipButton: { 
               behavior: ptp.pipButtonBehavior, 
               element: ptp.factories.simpleButtonFactory('pip', ptp.elementGetter('.ptp-more-options-control-panel-menu'), 
                   'ptp-control ptp-btn-control ptp-button-background ptp-btn-pip ' + 
                   'ptp-more-options-control-panel-menu-item ' + 
                   'ptp-more-options-menu-btn', 'PIP') 
           }, 
           socialButton: { 
               behavior: ptp.shareVideoButtonBehavior, 
               element: ptp.factories.simpleButtonFactory('shareVideo', ptp.elementGetter('.ptp-more-options-control-panel-menu'), 
                   'ptp-control ptp-btn-control ptp-button-background ptp-btn-share-video ' + 
                   'ptp-more-options-control-panel-menu-item ' + 
                   'ptp-more-options-menu-btn', 
                   'Share Video') 
           } 
       } 
   }; 
   
   SingleViewConfigurationObject = { 
       element: ptp.elementGetter(selector), 
       classNames: 'ptp-root-element', 
       behavior: ptp.singleViewBehavior, 
       logLevel: 0, 
       logOutput: null, 
       player: { 
           element: ptp.factories.simpleDivFactory('videoPlayer', ptp.elementGetter(selector), 
               'ptp-main-video-div-style ptp-background-style'), 
           behavior: ptp.videoBehavior, 
           autoPlay: true, 
           bufferingOverlay: { 
               behavior: ptp.bufferingOverlayBehavior, 
               element: ptp.createDiv('bufferingOverlay', ptp.elementGetter('.ptp-main-video-div-style'), 'ptp-buffering-overlay') 
           }, 
           errorMessagePanel: { 
               behavior: ptp.errorMessagePanelBehavior, 
               element: ptp.createDiv('errorMessagePanel', ptp.elementGetter('.ptp-main-video-div-style'), 'ptp-error-message-panel hidden') 
           }, 
           controlsDisabledInAd: //same as ptp.videoBehavior.setControlsDisabledInAd  
    mediaPlayerItemConfig: //same as ptp.videoBehavior.setMediaPlayerItemConfig  
      abrControlParameters: //same as ptp.videoBehavior.setAbrControlParameters  
     bufferControlParameters: //same as ptp.videoBehavior.setBufferControlParameters  
     ccVisibility: //same as ptp.videoBehavior.setCCVisibility  
      ccStyle: //same as ptp.videoBehavior.setCCStyle  
     mediaResource: //same as ptp.videoBehavior.setMediaResource  
     volume: //same as ptp.videoBehavior.setVolume 
     }, 
   
       pip: { 
           element: ptp.factories.simpleDivFactory('pip', ptp.elementGetter(selector), 'ptp-pip-video-div'), 
               behavior: ptp.videoBehavior, 
               bufferingOverlay: { 
               behavior: ptp.bufferingOverlayBehavior, 
                   element: ptp.createDiv('bufferingOverlay', ptp.elementGetter('.ptp-pip-video-div'), 'ptp-buffering-overlay') 
           }, 
           errorMessagePanel: { 
               behavior: ptp.errorMessagePanelBehavior, 
                   element: ptp.createDiv('errorMessagePanel', ptp.elementGetter('.ptp-pip-video-div'), 'ptp-error-message-panel hidden') 
           }, 
           autoPlay: false 
     }, 
       localization: DEFAULT_LOCALIZATION_CONFIG, 
       controlBar: DEFAULT_CONTROL_BAR_CONFIG, 
       audioTrackSelectionPanel: DEFAULT_AUDIO_TRACK_SELECTION_CONFIG, 
       closedCaptionLanguagePanel: DEFAULT_CLOSED_CAPTION_LANGUAGE_PANEL_CONFIG, 
       closedCaptionOptionsPanel: DEFAULT_CLOSED_CAPTION_OPTIONS_PANEL_CONFIG, 
       moreOptionsControlPanel: DEFAULT_MORE_OPTIONS_CONTROL_PANEL_CONFIG, 
       shareVideoPanel: DEFAULT_SHARE_VIDEO_PANEL_CONFIG 
   }; 
   
   MultiViewConfigurationObject = { 
       element: ptp.elementGetter(selector), 
       classNames: 'ptp-root-element', 
       behavior: ptp.multiViewBehavior, 
       logLevel: 0, 
       logOutput: null, 
       multiVideoHolder: { 
           element: ptp.factories.simpleDivFactory('multiViewPlayer', ptp.elementGetter(selector), 'ptp-multi-view-container') 
       }, 
       views: [ 
           { 
               player: {} // see in SingleViewConfigurationObject above 
     } 
       ], 
       localization: DEFAULT_LOCALIZATION_CONFIG, 
       controlBar: DEFAULT_CONTROL_BAR_CONFIG, 
       audioTrackSelectionPanel: DEFAULT_AUDIO_TRACK_SELECTION_CONFIG, 
       closedCaptionLanguagePanel: DEFAULT_CLOSED_CAPTION_LANGUAGE_PANEL_CONFIG, 
       closedCaptionOptionsPanel: DEFAULT_CLOSED_CAPTION_OPTIONS_PANEL_CONFIG, 
       moreOptionsControlPanel: DEFAULT_MORE_OPTIONS_CONTROL_PANEL_CONFIG, 
       shareVideoPanel: DEFAULT_SHARE_VIDEO_PANEL_CONFIG 
   };
   ```

* **ヘルパー構成** ：この構成は、次の要素で構成されます。

   * **ファクトリ** ビジュアル要素を作成するには、、、、お `ptp.factories.simpleButtonFactory`よびを `ptp.factories.simpleDivFactory`使用 `ptp.factories.simpleHRFactory`できま `ptp.factories.simpleSliderFactory`す。 詳しくは、 [UI Framework](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/index.html) APIドキュメントを参照してください。

   * **Mixins** Mixinは、共通の構成を使用するために動作で組み立てられる、組み合わせ可能なモジュールです。 例えば、多くのコンポーネントは、広告の再生中など、コンポーネントの動作に影響を与える可能性のある変更を認識したいと考えています。 これらの要素はすべて、クラスを追加 `adBreak` します。

      次に、組み込みミックスインの実装方法の例を示しま `adBreakStyling`す。

      ```js
      adBreakStyling = function (element, player) { 
          ... 
          ... 
          return composable().compose({ 
              init: init, 
              manageAdBreakStyle: manageAdBreakStyle 
       }); 
      }
      ```

      このミックスインを動作が使用する方法を次に示します。

      ```js
      customBehavior = function (element, configuration, player) { 
          var api = 
              component(element, configuration, player, clickHandler).compose( 
                  adBreakStyling(element, player).compose({ 
                      init: init, 
                  })); 
          return api; 
      }
      ```

      この例 `customBehavior` では、が公開するすべてのメソッドを使 `adBreakStyling`用できるようになりまし `manageAdBreakStyle`た。 追加の使用例の1つは、ミックスインがイベントリスナーを追加できる場合で、ハンドラー内でミックスインが何らかの方法で要素を変更できる場合です。 その後、このミックスインを使用するコンポーネントは、自動的にこの機能を持ちます。

   * **Utils** 設定セクションや `ptp.elementGetter`拡張で使用されるユーティリテ `ptp.deepmerge`ィなど、動作の記述や拡張に役立ちます。 詳しくは、 [UI Framework](https://help.adobe.com/en_US/primetime/api/psdk/btvsdk-ui-framework/index.html) APIドキュメントを参照してください。

