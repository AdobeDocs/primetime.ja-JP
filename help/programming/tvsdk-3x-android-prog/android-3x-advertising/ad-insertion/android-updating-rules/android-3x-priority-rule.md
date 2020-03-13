---
description: 優先度ルールは、VAST/VMAP応答からの再生用に選択される広告クリエイティブの優先順位を定義します。
keywords: priority rule;creative selection rules
seo-description: 優先度ルールは、VAST/VMAP応答からの再生用に選択される広告クリエイティブの優先順位を定義します。
seo-title: 優先度ルール
title: 優先度ルール
uuid: 20dd0ded-06dd-427d-8dd3-79f9f8a3390c
translation-type: tm+mt
source-git-commit: 3fdae2b6babb578d2cacff970fd9c7b53ad2c5dc

---


# 優先度ルール {#priority-rules}

優先度ルールは、VAST/VMAP応答からの再生用に選択される広告クリエイティブの優先順位を定義します。

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"><b>キー</b></th> 
   <th class="entry"><b>タイプ</b></th> 
   <th class="entry"><b>値</b></th> 
   <th class="entry"><b>説明</b></th>
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> priority</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td> 再生用にソースクリエイティブを選択する優先度を定義する小文字のMIMEタイプの配列。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> ホスト</span></td> 
   <td>現在、ホストのみ <span class="codeph"> がサポー</span> トされています。 この属性は、一致と値の属性が定義され <span class="codeph"> ている</span> 場合 <span class="codeph"> に必ず存在します</span> 。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 一致</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> multiple</span></td> 
   <td>可能な値：
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span> — 等しい</li> 
     <li><span class="codeph"> ne</span> — 次と等しくない</li> 
     <li><span class="codeph"> co</span> — 次を含む</li> 
     <li><span class="codeph"> nc</span> — 次を含まない</li> 
     <li><span class="codeph"> sw</span> — 次で始まる</li> 
     <li><span class="codeph"> ew</span> — 次で終わる</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> priority</span></td> 
   <td>値は常に優先度である必要があり <span class="codeph"> ます</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td> <p>TVSDKは、ソースクリエイティブの <span class="codeph"> 項目に対し</span> 、一致する属性を使用し <span class="codeph"></span> 、この配列に定義された値と照合します。</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 流れ</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td></td> 
   <td> <p>値はVODまたはラ <span class="codeph"> イブ</span> で <span class="codeph"> す</span></p> </td> 
  </tr> 
 </tbody> 
</table>

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "
<b>type</b>": "
<b>priority</b>",
                    "
<b>stream</b>": "vod",
                    "
<b>priority</b>": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    ...
                },
            ]
        }
    }
}
```
