---
description: 優先度ルールは、VAST/VMAP応答からの再生用に選択される広告クリエイティブの優先度順序を定義します。
keywords: 優先度ルール；クリエイティブ選択ルール
title: 優先順位ルール
translation-type: tm+mt
source-git-commit: 89bdda1d4bd5c126f19ba75a819942df901183d1
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---


# 優先順位規則{#priority-rules}

優先度ルールは、VAST/VMAP応答からの再生用に選択される広告クリエイティブの優先度順序を定義します。

**表1:Priorityルールには、次の属性と可能な値が含まれます。**

<table id="table_ljp_tgx_hz">  
 <thead> 
  <tr> 
   <th class="entry"> キー</th> 
   <th class="entry"> タイプ</th> 
   <th class="entry"> 値</th> 
   <th class="entry"> 説明</th> 
  </tr> 
 </thead>
 <tbody> 
  <tr> 
   <td><span class="codeph"> priority</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td> ソースクリエイティブを再生用に選択する優先度を定義する、小文字のMIME型の配列です。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> item</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> ホスト</span></td> 
   <td>現在、<span class="codeph"> host</span>のみがサポートされています。 <span class="codeph">が</span>と一致し、<span class="codeph">の値</span>が定義されている場合、この属性が存在する必要があります。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 一致</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> multiple</span></td> 
   <td>可能な値：
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span>  — 等しい</li> 
     <li><span class="codeph"> ne</span>  — 次に等しくない</li> 
     <li><span class="codeph"> co</span>  — 次を含む</li> 
     <li><span class="codeph"> nc</span>  — 次を含まない</li> 
     <li><span class="codeph"> sw</span> -開始</li> 
     <li><span class="codeph"> ew</span>  — 次で終わる</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> priority</span></td> 
   <td>値は常に<span class="codeph">優先度</span>にする必要があります</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> values</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td> <p>TVSDKは、ソースクリエイティブの<span class="codeph">アイテム</span>の<span class="codeph"> matches</span>属性を使用し、この配列で定義されている値と照合します</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 流れ</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td></td> 
   <td> <p>値は<span class="codeph"> vod</span>または<span class="codeph"> live</span>です</p> </td> 
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

