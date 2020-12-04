---
seo-title: Java APIを使用したポリシーの作成
title: Java APIを使用したポリシーの作成
uuid: c653548d-4abf-46b9-8669-d68b966da359
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Java API {#creating-a-policy-using-the-java-api}を使用したポリシーの作成

Java APIを使用してポリシーを作成するには、次の手順を実行します。

1. 開発環境を設定し、プロジェクト内の[開発環境の設定](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md)で説明されているすべてのJARファイルを含めます。
1. `com.adobe.flashaccess.sdk.policy.Policy`オブジェクトを作成し、権限、ライセンスキャッシュ期間、ポリシーの終了日などのプロパティを指定します。

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

1. `Policy`オブジェクトをシリアル化し、ファイルまたはデータベースに格納します。

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

このサンプルコードの完全なソースについては、リファレンス実装のコマンドラインツール「[!DNL samples]」ディレクトリの&#x200B;*com.adobe.flashaccess.samples.policy.CreatePolicy*&#x200B;を参照してください。
