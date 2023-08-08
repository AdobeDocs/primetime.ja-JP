---
title: 単一のテナント/ポリシーおよび複数のアプリケーションに対する CM の実装
description: 単一のテナント/ポリシーおよび複数のアプリケーションに対する CM の実装
source-git-commit: ac0c15b951f305e29bb8fa0bd45aa2c53de6ad15
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# 単一のテナント/ポリシーおよび複数のアプリケーションに対する CM の実装 {#imp-cm}



## 使用例

プログラマー P は、iPhoneアプリケーション、iPadアプリケーション、および Web サイトを持っています。 Adobe同時監視 (CM) と統合して、これらのアプリ間の同時ストリームの数を制限する必要があります。 プログラマーは、同時使用を制限するポリシーを作成します。 次の 2 つの例を見てみましょう。

最初のポリシーには、2 つ以下の同時ストリームを許可する 1 つのルールが含まれています。 最新のストリームを再生できます。
2 つ目のポリシーには、2 つのルールが含まれます。 2 台以下のデバイスからの同時ストリームを 3 つ以下にすることができ、最新のストリームの再生が許可されます。


## 1 つのルールを持つポリシー

最初のポリシーに含まれるルールは 1 つです。2 つ以上の同時ストリームを使用できません。3 つの同時ストリームが再生されている場合、開始する最初のストリームは停止します。

ストリームの開始には、2 つのアプリと 1 つの Web サイトが使用されます。

1. ユーザーがiPhoneアプリから 1 つのストリームを開始し、iPadアプリから 1 つのストリームを開始します。 このポリシーはこれを許可します。
1. 次に、ユーザはプログラマのウェブサイトから第 3 のストリームを開始する。
1. ポリシーのルール（最大 2 つのストリーム、最新の勝ち）では、最新のストリームを再生できます **最初に開始されたストリームは、ポリシーに準拠していないとマークされ、停止されます。**





<!---

Figure 1: Policy with one rule

 

A Policy with two Rules
The policy contains the following two rules: 

no more than 3 concurrent streams are allowed, the first stream to start will be stopped in case more than three concurrent streams are playing;
no more than 2 devices are allowed to play streams. The stream from the first device will be stopped in case streams are running from 3 devices.
 

In this use case two apps are used to start streams:

The user starts two streams (s1, s2) from the iPhone app which is installed on two different devices (dev1, dev2) and the policy permits it.
The user then starts a third stream from an iPad (dev3).
The rules in the policy allow the stream to start.
When the first stream will check its state, the second rule (max 2 devices, latest wins) will mark it as non-compliant with the policy and will stop playback.
 



Figure 2: Policy with two rules

 

For more information on policies, their "anatomy" and further use cases, please consult the Policy Decision Point topic. 

 

Prerequisites
In order to integrate with CM, a Zendesk ticket (https://adobeprimetime.zendesk.com) will have to be created and the following information specified:

the name of the company
the applications you want to integrate with CM. For each application, you are required to provide:
application name
application platform
the policy you want to enforce
 

After creating the ticket, the following information will be released for use:

type
description
example value
default value
endpoint    the endpoint for Adobe Concurrency Monitoring    
http://streams.adobeprimetime.com/v1/
http://streams.adobeprimetime.com/v1/
applicationId    iPhone app id    iphone54-75b4-431b-adb2-eb6b9e546013    -
applicationId    iPad app id    ipad5d54-75b4-431b-adb2-eb6b9e546013    -
applicationId    website app id    website4-75b4-431b-adb2-eb6b9e546013    -
interval for heartbeats    Interval in seconds to send heartbeat calls to Adobe Concurrency Monitoring    60    60
interval for stream compliance    Interval in seconds to check stream compliance in Adobe Concurrency Monitoring    180    180
 

Implementation Guidelines
The following items MUST be packaged in the application(s):

endpoint
application Id 
interval for heartbeats
interval for checking compliance
 

Glossary
 

We advise you to consult the Glossary for definitions of terms used in the present cookbook.

 

Workflows
 



Figure 3: Concurrency Monitoring Workflows (described below)

 

1. Concurrency Monitoring allows playback
Step    APIs    Description    Comments
1    N/A    user starts video playback    
Prerequisites:

user is authenticated with an MVPD

2    API call: Session initialization    the app/player calls CM to initiate a stream    the app/player sends all required metadata using information from Adobe Primetime Authentication
3    CM responds with decision and streamId    
the streamId json node value is stored by the application for the duration of the video playback

the policyCompliant json node has the value true so the app/player starts playback

the heartbeat url is returned by the call as a JSON Hypertext Application Language(HAL) template

4    N/A    the app/player starts video playback    N/A
5    API call: Heartbeat call - event=alive    the app/player reports alive heartbeats every x seconds    
the x value is specified by Adobe in the Zendesk ticket at integration

the url to report heartbeats is taken from the response of the start stream call and the value for the event param is alive

6    API call: Check Stream Compliance    the app/player checks the stream status every n seconds    
the n value is specified by Adobe in the Zendesk ticket at integration

stream status check is performed to validate that Adobe Concurrency Monitoring is allowing playback

7    CM responds with decision to continue playback    the policyCompliant json node has value true so the app/player continues playback
8    N/A    the app/player continues to show the video stream to the user    N/A
9    API call - Heartbeat call - alive=stop    the app/player sends stop heartbeat when the video finishes    the url to report heartbeats is taken from the response of the start stream call and the value for the event param is stop
 

Steps 5,6,7,8 will be performed in a loop until the video stream is stopped.

 

 

2. Concurrency Monitoring denies playback after stream is started
Step    APIs    Description    Comments
1    N/A    user starts video playback    
Prerequisites:

user is authenticated with an MVPD

2    API call: Session initialization    the app/player calls CM to initiate a stream    the app/player send all required metadata using information from Adobe Primetime Authentication
3    CM responds with decision and streamId    
the streamId json node value is stored by the application for the duration of the video playback

the policyCompliant json node has value true so the app/player starts playback

the heartbeat url is returned by the call as a JSON Hypertext Application Language(HAL) template

4    N/A    the app/player starts video playback    N/A
5    API call: Heartbeat call - event=alive    the app/player reports alive heartbeats every x seconds    
the x value is specified by Adobe in the Zendesk ticket at integration

the url to report heartbeats is taken from the response of the start stream call and the value for the event param isalive

6    API call: Check Stream Compliance    the app/player checks the stream status every n seconds    
the n value is specified by Adobe in the Zendesk ticket at integration

stream status check is performed to validate that Adobe Concurrency Monitoring is allowing playback

7    CM responds with decision to stop playback    the policyCompliant json node has value false so the app/player stops playback
8    N/A    the app/player stops the video stream and displays an error to the user    N/A
9    API call - Heartbeat call - alive=stop    the app/player sends a stop heartbeat    the url to report heartbeats is taken from the response of the start stream call and the value for the event param is stop
 
3. Concurrency Monitoring doesn't allow playback
Step    APIs    Description    Comments
1    N/A    user starts video playback    
Prerequisites:

user is authenticated with an MVPD

2    API call: Session initialization    the app/player calls CM to initiate a stream    the app/player send all required metadata using information from Adobe Primetime Authentication
3    CM responds with decision and streamId    
the policyCompliant json node has value false so the app/player does NOT start playback

4    N/A    
the app/player does NOT start video playback

it displays an error message to the user

N/A
 

 
Description of the API calls
Session initialization call
 

The responsibility of the application developer is to:

Initialize a stream with Concurrency Monitoring before starting video playback
check that the response of the call contains the node policyCompliant with value true
start video playback
 

API Console - initialize session

 

name
value
obtained from
endpoint    
http://streams.adobeprimetime.com/v1/
Zendesk ticket at integration

HTTP method    POST    documentation
URI path template    [appID]/[mvpd]/accounts/[account_id]/streams    N/A
Parameter values
name
value example
where to use it
obtained from
applicationId    iphone54-75b4-431b-adb2-eb6b9e546013    uri    Zendesk ticket at integration
mvpdName    Sample_MVPD    uri    
Adobe Primetime Authentication from config endpoint when user selects the MVPD

accountId    12345    uri    
Adobe Primetime Authentication upstreamUserID metadata after user login

User Metadata upstreamUserID - Adobe Primetime Authentication

programmerName    Sample_Programmer_Id    form parameter    Adobe Primetime Authentication
channel    CHANNEL    form parameter    Adobe Primetime Authentication
deviceId    30fe8d0f-35d4-4082-a728-405fcbae5ddb    form parameter    Adobe Primetime Authentication
 

 
Session initialization - example

```
-data 'programmer=PROGRAMMER_ID&device_id=30fe8d0f-35d4-4082-a728-405fcbae5ddb&channel=CHANNEL' 'http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams'
 
> POST /v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams HTTP/1.1
> Host: streams.adobeprimetime.com
> Accept: */*
> Content-Type: application/x-www-form-urlencoded; charset=UTF-8
> Content-Length: 101
>
< HTTP/1.1 201 Created
< Date: Thu, 06 Aug 2015 08:56:47 GMT
< Cache-Control: no-cache, no-store, max-age=0, must-revalidate
< Pragma: no-cache
< Expires: 0
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Methods: GET
< Access-Control-Allow-Methods: POST
< Access-Control-Allow-Methods: OPTIONS
< Access-Control-Allow-Methods: HEAD
< Access-Control-Allow-Methods: PUT
< Access-Control-Allow-Methods: DELETE
< Access-Control-Allow-Headers: Content-Type
< Location: http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4
< Content-Type: application/json; charset=UTF-8
< Content-Length: 511
< Age: 0

{
  "_links": {
    "self": {
      "href": "
    },
    "heartbeat": {
      "href": ",
      "templated": true
    }
  },
  "streamId": "ff__-sE4",
  "streamStart": 1438850042533,
  "policyCompliant": true
```


Heartbeat call - event=alive


The responsibility of the application developer is to:

Send heartbeats at the required interval in seconds. The interval will be specified in the Zendesk ticket. 
 
name
example value
obtained from
endpoint    
http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4
session initialization call

_links.heartbeat.href
HTTP method    POST    documentation
Parameter values
name
value example
where to use it
obtained from
event    alive    GET parameter    documentation
 

 
Heartbeat call - example
 
curl -v -X POST 'http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4?event=alive'

```
> POST /v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4?event=alive HTTP/1.1
> Host: streams.adobeprimetime.com
> Accept: */*
>
< HTTP/1.1 202 Accepted
< Date: Thu, 06 Aug 2015 14:19:54 GMT
< Cache-Control: no-cache, no-store, max-age=0, must-revalidate
< Pragma: no-cache
< Expires: 0
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Methods: GET
< Access-Control-Allow-Methods: POST
< Access-Control-Allow-Methods: OPTIONS
< Access-Control-Allow-Methods: HEAD
< Access-Control-Allow-Methods: PUT
< Access-Control-Allow-Methods: DELETE
< Access-Control-Allow-Headers: Content-Type
< Content-Length: 0
< Age: 0
```
 
Check Stream Compliance 
The responsibility of the application developer is to:

Call the API at required interval in seconds. The interval will be specified in the Zendesk ticket. 
Stop video playback if the policyCompliant json node has value false
Send heartbeat to stop stream Heartbeat call to stop stream
 

API Console - current state of the stream resource

name
example value
obtained from
endpoint    
http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4
session initialization call

_links.self.href
HTTP method    GET    documentation
Parameter values
name
value example
where to use it
obtained from
mvpdName    Sample_MVPD    uri    
Adobe Primetime Authentication from config endpoint when user selects the MVPD

accountId    12345    uri    
Adobe Primetime Authentication upstreamUserID metadata after user login

User Metadata upstreamUserID - Adobe Primetime Authentication

 

Check Stream Compliance - example
curl 'http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4'

```
> POST /v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4 HTTP/1.1
> Host: streams.adobeprimetime.com
> Accept: */*
> Content-Type: application/x-www-form-urlencoded; charset=UTF-8
> Content-Length: 30
>
< HTTP/1.1 200 Created
< Date: Thu, 06 Aug 2015 08:56:47 GMT
< Cache-Control: no-cache, no-store, max-age=0, must-revalidate
< Pragma: no-cache
< Expires: 0
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Methods: GET
< Access-Control-Allow-Methods: POST
< Access-Control-Allow-Methods: OPTIONS
< Access-Control-Allow-Methods: HEAD
< Access-Control-Allow-Methods: PUT
< Access-Control-Allow-Methods: DELETE
< Access-Control-Allow-Headers: Content-Type
< Location: http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4
< Content-Type: application/json; charset=UTF-8
< Content-Length: 511
< Age: 0
```

```
{
  "_links": {
    "self": {
      "href": "
    },
    "heartbeat": {
      "href": ",
      "templated": true
    }
  },
  "streamId": "ff__-sE4",
  "streamStart": 1438850042533,
  "policyCompliant": true
}
```

Heartbeat call - alive=stop
name
example value
obtained from
endpoint    
http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4
session initialization call

_links.heartbeat.href
HTTP method    POST    documentation
Parameter values
name
value example
where to use it
obtained from
event    stop    GET parameter    documentation
 

Heartbeat call - example
curl -v -X POST 'http://streams.adobeprimetime.com/v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4?event=stop'

```
> POST /v1/iphone54-75b4-431b-adb2-eb6b9e546013/MVPD_ID/accounts/12345/streams/f__-sE4?event=stop HTTP/1.1
> Host: streams.adobeprimetime.com
> Accept: */*
>
< HTTP/1.1 202 Accepted
< Date: Thu, 06 Aug 2015 14:19:54 GMT
< Cache-Control: no-cache, no-store, max-age=0, must-revalidate
< Pragma: no-cache
< Expires: 0
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Methods: GET
< Access-Control-Allow-Methods: POST
< Access-Control-Allow-Methods: OPTIONS
< Access-Control-Allow-Methods: HEAD
< Access-Control-Allow-Methods: PUT
< Access-Control-Allow-Methods: DELETE
< Access-Control-Allow-Headers: Content-Type
< Content-Length: 0
< Age: 0
```

Related Information
Introduction - Adobe Concurrency Monitoring
API Console - Adobe Concurrency Monitoring
User Metadata - Adobe Primetime Authentication
--->
