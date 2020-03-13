---
description: TVSDKメソッドを呼び出してメディアを一時停止および再生するボタンを設定できます。
seo-description: TVSDKメソッドを呼び出してメディアを一時停止および再生するボタンを設定できます。
seo-title: 再生/一時停止ボタンの実装
title: 再生/一時停止ボタンの実装
uuid: eccdce4b-0114-4389-b5ee-74fe62d38ed8
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68

---


# 再生/一時停止ボタンの実装{#implement-a-play-pause-button}

TVSDKメソッドを呼び出してメディアを一時停止および再生するボタンを設定できます。

再生ボタンまたは一時停止ボタンを実装するには、次のサンプルコードを使用します。

<!--<a id="example_BC2632D673FE451190A30A23145090D0"></a>-->

```
_playPauseButton =  
[[UIButton alloc] initWithFrame:CGRectMake(BUTTON_POS_X, BUTTON_POS_Y, BUTTON_SIZE_W, BUTTON_SIZE_H)]; 
[_playPauseButton setImage:[UIImage imageNamed:@"play.png"] forState:UIControlStateNormal];  
[_playPauseButton setImage:[UIImage imageNamed:@"pause.png"] forState:UIControlStateSelected]; 
[_playPauseButton addTarget:self action:@selector(playTouch:) forControlEvents:UIControlEventTouchUpInside]; 
[self addSubview:_playPauseButton]; 
 
... 
 
- (void)playTouch:(id)sender { 
    if (self.player.status == PTMediaPlayerStatusPlaying) { 
        _playPauseButton.selected = YES;  
        [self.player pause]; 
    } 
    else { 
        _playPauseButton.selected = NO; [self.player play]; 
    } 
} 
```

