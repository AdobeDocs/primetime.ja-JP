---
description: AdobeTVSDKConfig.jsonでは、特定のゾーンのルールと同様に、デフォルトのルールを指定できます。
seo-description: AdobeTVSDKConfig.jsonでは、特定のゾーンのルールと同様に、デフォルトのルールを指定できます。
seo-title: クリエイティブ選択ルールの例
title: クリエイティブ選択ルールの例
uuid: 7b4b4a76-f813-4f6c-ac41-36ca08bb8173
translation-type: tm+mt
source-git-commit: 5908e5a3521966496aeec0ef730e4a704fddfb68
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# クリエイティブ選択ルールの例{#sample-creative-selection-rules}

`AdobeTVSDKConfig.json`では、既定の規則と特定のゾーンの規則を指定できます。

## デフォルトのルールの例{#section_xy4_3fx_hz}

次の例は、デフォルトのルールのみを定義する`AdobeTVSDKConfig.json`ファイルの例です。

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "type": "priority",
                    "stream": "vod",
                    "priority": [
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
                    "type": "priority",
                    "stream": "live",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "normalize",
                    "item": "host",
                    "matches": "ew",
                    "values": [
                        "redirector.gvt1.com"
                    ],
                    "find": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "replace": "videoplayback/$1/expire//$2/signature//"
                }
            ]
        }
    }
}
```

## 追加のゾーン規則{#section_ocv_3fx_hz}を含むデフォルトの規則の例

次の例は、デフォルトの規則を定義する[!DNL AdobeTVSDKConfig.json]ファイルの例で、特定のゾーンIDに対する追加の規則（この場合は、ゾーン&#x200B;**&quot;1234&quot;**）を示しています。

```
{
    "ads": {
        "rules": {
            "default": [
                {
                    "type": "priority",
                    "stream": "vod",
                    "priority": [
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
                    "type": "priority",
                    "stream": "live",
                    "priority": [
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "video/mp4",
                        "video/m4v",
                        "video/x-flv",
                        "video/webm"
                    ]
                },
                {
                    "type": "normalize",
                    "item": "host",
                    "matches": "ew",
                    "values": [
                        "redirector.gvt1.com"
                    ],
                    "find": "videoplayback/(.*?)/expire/.*?/(.*?)/signature/.*?/",
                    "replace": "videoplayback/$1/expire//$2/signature//"
                }
            ],
            
<b>"1234"</b>: [
                {
                    "type": "priority",
                    "matches": "nc",
                    "item": "host",
                    "values": [
                        "my.domain.com",
                        "a.bcd.com"
                    ],
                    "priority": [
                        "application/x-shockwave-flash",
                        "video/mp4",
                        "video/x-flv",
                        "video/quicktime",
                        "video/webm",
                        "application/x-mpegurl",
                        "application/vnd.apple.mpegurl",
                        "application/javascript"
                    ]
                }
            ]
        }
    }
}
```

