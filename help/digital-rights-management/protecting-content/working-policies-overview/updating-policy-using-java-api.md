---
seo-title: Java APIを使用したDRMポリシーの更新
title: Java APIを使用したDRMポリシーの更新
uuid: ec21351c-900e-48f5-845a-c0b430c210d7
translation-type: tm+mt
source-git-commit: 29bc8323460d9be0fce66cbea7c6fce46df20d61

---


# Java APIを使用したDRMポリシーの更新 {#updating-a-drm-policy-with-the-java-api}

Java APIを使用してDRMポリシーを更新するには：

1. 開発環境を設定し、「開発環境の設定」に記載されているすべてのJARファイルをプロジ [ェクトに含めます](../../protecting-content/setting-up-the-sdk/setup-dev-env.md)。
1. DRMインスタンスを作 `Policy` 成し、ファイルまたはデータベースからDRMポリシーを読み取ります。

   ```
   Policy policy = new Policy(policyBytes);
   ```

1. DRMオブジェクトの名 `Policy` 前や使用ルールなどのプロパティを設定して、DRMオブジェクトを更新します。

   ```java
   // Change the DRM policy name.  
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

1. 更新したDRMオブジェクトをシ `Policy` リアライズし、ファイルまたはデータベースに保存します。

   ```java
   // Serialize the DRM policy.  
   byte[] policyBytes = policy.getBytes();  
   System.out.println("New DRM policy revision number: "  
       +  policy.getRevision());      
   // Write the DRM policy to a file.   
   // Alternatively, the DRM policy may be stored in a database.  
   FileOutputStream out = new FileOutputStream("demopolicy-updated.pol");  
   out.write(policyBytes);  
   out.close();
   ```

このサン `com.adobe.flashaccess.samples.policy.UpdatePolicy` プルコードのソースについては、Reference Implementation Command Line Tools [!DNL samples] ディレクトリのを参照してください。
