---
seo-title: Java APIを使用したポリシーの更新
title: Java APIを使用したポリシーの更新
uuid: 23c50f05-799e-4f5a-869b-4b5e29a36ce1
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Java APIを使用したポリシーの更新 {#updating-a-policy-using-the-java-api}

Java APIを使用してポリシーを更新するには、次の手順を実行します。

1. 開発環境を設定し、「プロジェクト内の開発環境の設定」に記載されてい [るすべてのJARファイルを](../../aaxs-protecting-content/content-setting-up-the-sdk/content-setting-up-the-dev-env.md) 含めます。
1. インスタンスを `Policy` 作成し、ファイルまたはデータベースからポリシーを読み取ります。

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. 名前や使 `Policy` 用ルールなどのプロパティを設定して、オブジェクトを更新します。

   ```java
     // Change the policy name.  
     policy.setName("UpdatedDemoPolicy");  
   
     // Add DRM module restrictions to the play right  
     for (Right r: policy.getRights()) {  
      if (r instanceof PlayRight) {  
       PlayRight pr = (PlayRight) r;  
       // Disallow Linux versions up to and including 1.9.  Allow  
       // all other OSes and Linux versions above 1.9  
       VersionInfo toExclude = new VersionInfo();  
       toExclude.setOS("Linux");  
       toExclude.setReleaseVersion("1.9");  
       Collection<VersionInfo> exclusions = new ArrayList<VersionInfo>();  
       exclusions.add(toExclude);  
       ModuleRequirements drmRestrictions = new ModuleRequirements();  
       drmRestrictions.setExcludedVersions(exclusions);  
       pr.setDRMModuleRequirements(drmRestrictions);  
       break;  
      }  
     }
   ```

1. 更新したオブジェクトをシ `Policy` リアライズし、ファイルまたはデータベースに保存します。

   ```java
      // Serialize the policy.  
      byte[] policyBytes = policy.getBytes();  
      System.out.println("New policy revision number: "  
       +  policy.getRevision());      
      // Write the policy to a file.   
      // Alternatively, the policy may be stored in a database.  
      FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
      out.write(policyBytes);  
      out.close(); 
   ```

このサンプルコードの完全なソースについては、『リファレンス導入コ `com.adobe.flashaccess.samples.policy.UpdatePolicy` マンドラインツール』の「samples」ディレクトリを参照してください。
