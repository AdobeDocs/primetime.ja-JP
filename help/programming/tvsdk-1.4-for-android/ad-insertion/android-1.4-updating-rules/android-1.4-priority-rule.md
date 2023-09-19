---
description: 優先度ルールは、VAST/VMAP 応答からの再生用に選択される広告クリエイティブの優先度順を定義します。
keywords: 優先順位ルール；クリエイティブ選択ルール
title: 優先度ルール
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# 優先度ルール{#priority-rules}

優先度ルールは、VAST/VMAP 応答からの再生用に選択される広告クリエイティブの優先度順を定義します。

**表 1：優先度ルールには次の属性と可能な値があります。**

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
   <td><span class="codeph"> 優先度</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td> 再生用にソースクリエイティブを選択する必要がある優先度を定義する、小文字の MIME タイプの配列。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 項目</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> ホスト</span></td> 
   <td>現在のみ <span class="codeph"> ホスト</span> はサポートされています。 この属性は、 <span class="codeph"> 一致する</span> および <span class="codeph"> 値</span> 属性が定義されている。</td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 一致する</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> 複数</span></td> 
   <td>可能な値：
    <ul id="ul_tnf_2hx_hz"> 
     <li><span class="codeph"> eq</span>  — 等しい</li> 
     <li><span class="codeph"> ne</span>  — 等しくない</li> 
     <li><span class="codeph"> co</span>  — 次を含む</li> 
     <li><span class="codeph"> nc</span>  — 次を含まない</li> 
     <li><span class="codeph"> sw</span>  — で始まる</li> 
     <li><span class="codeph"> ew</span>  — で終わる</li> 
    </ul></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> type</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td><span class="codeph"> 優先度</span></td> 
   <td>値は常に <span class="codeph"> 優先度</span></td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> 値</span></td> 
   <td><span class="codeph"> 配列</span></td> 
   <td></td> 
   <td> <p>TVSDK は、 <span class="codeph"> 一致する</span> 属性 <span class="codeph"> 項目</span> ソースクリエイティブの。この配列で定義された値と一致します</p> </td> 
  </tr> 
  <tr> 
   <td><span class="codeph"> ストリーム</span></td> 
   <td><span class="codeph"> 文字列</span></td> 
   <td></td> 
   <td> <p>値は <span class="codeph"> vod</span> または <span class="codeph"> live</span></p> </td> 
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
