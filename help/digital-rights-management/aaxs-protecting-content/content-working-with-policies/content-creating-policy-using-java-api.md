---
title: Java API を使用したポリシーの作成
description: Java API を使用したポリシーの作成
copied-description: true
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---

# Java API を使用したポリシーの作成 {#creating-a-policy-using-the-java-api}

Java API を使用してポリシーを作成するには、次の手順を実行します。

1. 開発環境を設定し、 [開発環境の設定](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) を選択します。
1. の作成 `com.adobe.flashaccess.sdk.policy.Policy` オブジェクトを作成し、権限、ライセンスキャッシュ期間、ポリシー終了日などのプロパティを指定します。

   ```java
     // Create a new Policy object.  
     // False indicates the policy does not use license chaining.  
     Policy policy = new Policy(false);  
   
     policy.setName("DemoPolicy");  
   
     // Specify that the policy requires authentication to obtain a license.  
     policy.setLicenseServerInfo  
      (new LicenseServerInfo(AuthenticationType.UsernamePassword));  
   
     // A policy must have at least one Right, typically the play right  
     PlayRight play = new PlayRight();  
   
     // Users may only view content for 24 hours.  
     play.setPlaybackWindow(24L * 60 * 60);  
   
     // Add the play right to the policy.  
     List<Right> rightsList = new ArrayList<Right>();  
     rightsList.add(play);  
     policy.setRights(rightsList);  
   
     // Licenses may be stored on the client for 7 days after downloading  
     policy.setLicenseCachingDuration(7L * 24 * 60 * 60);  
     try {  
      // Content will expire December 31, 2010  
      SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");  
      policy.setPolicyEndDate(dateFormat.parse("2010-12-31"));  
     } catch (ParseException e) {  
      // Invalid date specified in dateFormat.parse()  
      e.printStackTrace();  
     }
   ```

1. をシリアル化します。 `Policy` オブジェクトを作成し、ファイルまたはデータベースに保存します。

   ```java
     // Serialize the policy  
     byte[] policyBytes = policy.getBytes();  
     System.out.println("Created policy with ID: " + policy.getId());  
   
     // Write the policy to a file.   
     // Alternatively, the policy may be stored in a database.  
     FileOutputStream out = new FileOutputStream("demopolicy.pol");  
     out.write(policyBytes);  
     out.close();
   ```

このサンプルコードの完全なソースについては、 *com.adobe.flashaccess.samples.policy.CreatePolicy* （「参照実装」コマンドラインツール） [!DNL samples]&quot;ディレクトリ。
