# ANDROID CICD ON JENKINS

> **Required Plugins**

```
Jenkins Recommended Plugins
Android Signing Plugin
Google Play Android Publisher
```

> **Adding Path Variable**

```
Go to ManageJenkins -> Global Properties -> Check Environment Variables Add Path for ANDROID SDK AND ZIPALIGN
```

![image](https://user-images.githubusercontent.com/71398798/149320635-c7ed3dd6-38c4-46e5-b021-a9fd4eb15eca.png)

```
Go to ManageJenkins -> Global Configuration Tool -> JDK -> Add JDK
```

![image](https://user-images.githubusercontent.com/71398798/149320896-759974f3-c487-45a4-9a17-ed37789bcbee.png)

```
After Adding the required ENV Path Restart Jenkins Server.

```


> **Creating Pipeline**

```
Go to Dashboard -> New Item -> FreeStyle Project
```
![image](https://user-images.githubusercontent.com/71398798/149321331-d633163b-8d2a-4df9-a828-31c4e5520e42.png)

```
In General  Add Log Rotation to Discard Old builds at one day time notice (OPTIONAL)
```
![image](https://user-images.githubusercontent.com/71398798/149321497-4182241b-9169-48f6-adf1-b898df44eebf.png)

```
UNDER SCM ADD GIT OR GITHUB AND ADD YOUR REPO AND CREDENTIALS IF REQUIRED
```
![image](https://user-images.githubusercontent.com/71398798/149321592-52dc223c-eb3f-4efa-94d1-84304226de8d.png)


```
Under Branches to Build specify your build branch
```

![image](https://user-images.githubusercontent.com/71398798/149321663-c12ffdec-6d38-40d6-8f77-9f6b849400ff.png)


```
Add trigger to Trigger build only if its successful and stable
```

![image](https://user-images.githubusercontent.com/71398798/149321748-037099c6-0436-469c-9b3c-74930ff26157.png)


```
Under Build Step add GRADLE 
```
![image](https://user-images.githubusercontent.com/71398798/149321832-f0929a89-130c-4549-b5d0-9d5f9743fce2.png)


```
Add Another Build Step and provide Sign Android APKs task
```

![image](https://user-images.githubusercontent.com/71398798/149321932-7eb0bcbb-e83f-482e-ab71-0ae4b5ce6960.png)


```
Add your keystore file in P12 format if you have keystore in jks format use keytool to convert it into p12

keytool -importkeystore -srckeystore <yourkeystore.jks> -srcstoretype JKS -deststoretype PKCS12 -destkeystore <yourkeystore.p12>
```

```
Under Post Build Action Add Archive Artifact option and provide wildcard for .apk and .aab files
```

![image](https://user-images.githubusercontent.com/71398798/149322250-fa2bdc58-8419-40e3-9346-2bae0b5ca3dc.png)


```
Under Post Build Action add Publish Google Play Task
```

![image](https://user-images.githubusercontent.com/71398798/149322373-35c21aea-7fe6-4549-acb1-66fa2368432f.png)

